pipeline {
    agent any
    tools {

    }
    parameters{
        choice(name:'VERSION',choices:['1.1.0','1.1.1'],description:'')
        booleanParam(name:'executeTests',defaultValue:true,description:'')
    }
    stages{
        stage("init"){
            steps{
                script{
                    gv= load("script.groovy")
                }
            }
        }
        stage("build"){
            steps{
                gv.buildApp()
            }
        }
        stage("test"){
            when{
                expression{
                    params.executeTests
                }
            }
             steps{
                gv.testApp()
            }

        }
        stage("deploy"){
             steps{
                script{
                   gv.buildApp() 
                }
            }

        }
    }
}