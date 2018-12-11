pipeline {			
      agent {			
     			
     	label 'buildconductor-bpm'					
     			
     stages {     			
         			
         stage('Build') {      			        			
             steps {			                                			
             	sh '/buildconductor/bpm/run-automation.sh buildBpm HW 0.78 Main 10.0.10.166 20005 ghodgkinson ghodgkinson Staging ghodgkinson passw0rd ${BUILD_NUMBER} ${BUILD_URL} ${NODE_NAME}'               			
             }			
         }			
         			
         stage('Publish to UCD') {			
         	steps {			       				 			
         	      sh '/buildconductor/bpm/run-automation.sh uploadToUcd "HelloWorld Process App BPMStandard8.5" ${BUILD_NUMBER} output *.zip admin admin ${BUILD_URL} https://10.0.10.47:8446'            			
             }                        	 				
         }	
           
         stage('Trigger UCD Dev Deploy') {			
            steps {			       				 			
         	      sh '/buildconductor/bpm/run-automation.sh requestProcess "Demo Applications System (BPM, IIB, WDP, WAS)" "Dev" "Deploy HelloWorld Process App BPMStandard8.5 (Latest Version)" admin admin ${BUILD_URL} https://10.0.10.47:8446'            			
             }                        	 				
         }
     }			
 } 
