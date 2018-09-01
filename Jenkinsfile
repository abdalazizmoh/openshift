openshift.withCluster() {
 openshift.withCredentials('cluster-admin-credential-id') {
  def PROJECT_NAME = "new-project"
  def cm


  openshift.withProject(PROJECT_NAME) {

   echo "Hello from project ${openshift.project()} in cluster ${openshift.cluster()}"

    stage('Checkout') {

      // Get some code from a GitHub repository
      git branch: "master", url: cm.data['fis-1-app-git-url']
     }
     	// Mark the code build 'stage'....
    stage('Maven Build') {
	     // Run the maven build
	     sh "mvn clean compile -s settings.xml"
    }
    stage('Deploy to DEV') {
	    //echo "Deleting OLD JDG Env if exist"
	    //openshift.selector( 'all', [ application: cm.data['fis-1-app-name'] ] ).delete()
	    //openshift.selector( 'pvc', [ application: cm.data['fis-1-app-name'] ] ).delete()
     	// Run the fabric8
     	sh "mvn fabric8:deploy -s settings.xml"
    }

   }

  }

 }
}
