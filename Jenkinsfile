def label = "pl_scripted_dhc-${UUID.randomUUID().toString()}"
def image_name = "stuartcbrown/jentest:${label}"
        //label below is set in the the chared cloud conig
    node('lbl_docker_pod_dnd') {
        container("docker") {
            stage("docker") {
                checkout scm
                echo image_name
                withCredentials([usernamePassword(credentialsId: 'dockerhubstu', passwordVariable: 'PASSWORD', usernameVariable: 'USER')]) {


                    sh 'docker login -p ${PASSWORD} -u ${USER}'
                    sh "docker build . -t $image_name"
                    sh "docker push $image_name"

                }
            }
        }
    }
}
