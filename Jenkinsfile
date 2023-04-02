pipeline {
    agent {
        node { label: "maven" }
    }
    environment { QUAY = credentials('QUAY_USER') }
    stages {
        stage("Unit Tests") {
           steps {
             sh "mvn verify"
           }
        }
        stage("Build & Push Image") {
            steps {
                sh '''
                    ./mvnw quarkus:add-extension \
                    -Dextensions="container-image-jib"
                '''
                sh '''
                    ./mvnw package -DskipTests \
                    -Dquarkus.jib.base-jvm-image=quay.io/redhattraining/do400-java-alpine-openjdk11-jre:latest \
                    -Dquarkus.container-image.build=true \
                    -Dquarkus.container-image.registry=quay.io \
                    -Dquarkus.container-image.group=velrajarichandran \
                    -Dquarkus.container-image.name=do400-deploying-lab \
                    -Dquarkus.container-image.username=velrajarichandran \
                    -Dquarkus.container-image.password="Velammal#55" \
                    -Dquarkus.container-image.tag=build-${BUILD_NUMBER} \
                    -Dquarkus.container-image.additional-tags=latest \
                    -Dquarkus.container-image.push=true
                '''

            }

        }

    }

}
