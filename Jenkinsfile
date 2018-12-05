pipeline{
   agent any
    stages 

	{ 
		stage("hello")
		{
			steps{
				sh """
					echo "hello im going to start"
					"""
			     }
		}
		stage("testing")
                {
                        steps{
                                sh """
                                        echo " im testing"
                                        """
                             }
                }



		stage("docker build"){
			steps{
				sh """
					docker build -t koochetti/nginx .
				"""
			}
		}
		stage("push to DTR"){
			steps{
			withCredentials([usernamePassword(credentialsId: 'dp', usernameVariable: 'USER', passwordVariable: 'PASSWORD')])
			{
				sh """
					docker login --username $USER --password $PASSWORD
					docker push koochetti/nginx
				"""
			}


		stage("ready to diploy")
                {
                        steps{
                                sh """
                                        echo "im ready to diploy"
                                        """
                             }
                }

		
		   }

              }
		
	}
}
