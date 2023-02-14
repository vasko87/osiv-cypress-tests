pipeline {

    agent any 
    
     parameters{
        string(name: 'SPEC', defaultValue: "cypress/e2e/**/**", description: "Enter the script path you want to execute")
        choice(name: 'BROWSER', choices: ['chrome'], description: "Choice the browser where you want ot execute your scrips")
        choice(name: 'BASEURL', choices:["https://osiv-frtest.ivnet.ch", "https://osiv-nrtest.ivnet.ch", "https://osiv-devpbr.ivnet.ch"], description: "Choice the URL where you want to execute you scripts")
     }


    stages {
        stage('Building'){
            steps{
               echo "Building the application"
               bat "npm install cypress"
               bat "npm audit fix"
            }
           
                }
        stage('Testing'){
            steps{
                bat "npx cypress run --env ENV=${ENVIROMENT} --browser ${BROWSER} --spec ${SPEC} --record --key 419a7ab6-1abe-46ec-949c-2d09259a76f2"    
            }
        }
        stage('Deploying'){
            steps{
                echo "Deploy the application"
            }
             
        }

    }

                
}