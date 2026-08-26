pipeline{
    agent any
    stages{
        stage('Checkout'){
            steps{
              checkout scm
            }
        }
      stage('Run Newman'){
        steps{
                bat '''newman run "Reqres Product.postman_collection.json"^ -e "restfulapi.postman_environment.json" ^ -r cli,htmlextra ^ --reporter-htmlextra-export "newman-report.html" '''
            }
        }
    }
    
}
