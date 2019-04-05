@Library('EPC_Libraries')

variable_map = globalVariables("buildConfig")
String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""

pipeline{
    agent any
    options { 
        buildDiscarder(logRotator(numToKeepStr: '10')) 
    }
    triggers { pollSCM(cron_string) }
    parameters {
        choice(
            name: 'WHITELABEL',
            choices: "lotus\nkaarmana",
            description: 'Select whitelabel' )
    }
    stages{
        stage("Build-Test-Register"){
          steps{
            sh 'echo "WHITELABEL: $WHITELABEL"'
          }
        }       
    }
}
