

    pipeline {

        agent {
            node {
                label 'DotNetCore'
            }
        }

        
     parameters {
                    booleanParam(defaultValue: false,
                    name: 'FULL_BUILD',
                    description: 'Run a Full Build of the application. Includes SonarQube and marking a package as Release Ready')

                    booleanParam(defaultValue: false,
                    name: 'BLACKDUCK_BUILD',
                    description: 'Run a BLACK DUCK Scan of the application')

                    booleanParam(defaultValue: false,
		            name: 'VERACODE_BUILD',
		            description: 'Run a Veracode Build of the application')

        }
        
      environment {
        COMPONENT="HELLO"   
          
          
      }

      triggers {

            parameterizedCron(env.BRANCH_NAME == 'main' ? '''
            02 13 * * 4 %VERACODE_BUILD=true;
            ''' : '')
        }

        stages {
                    
	stage('Blocked') {
             when {
                    
                    expression { params.VERACODE_BUILD }
                } 

                steps {
                    
                        powershell '''

     
                            Write-host "This job is blocked"

                        '''
                    
                }
            }
          
  


        }//end of stages

   //end of post

    } //end of pipeline
