node {

  def sonarServer = 'BaseLine'
  def jobWorkspace = pwd()
  def branch = ''
  def installFlag = false


  if ( jobWorkspace.contains("buildBranch") ) {
        installFlag = true
    } else {
        sonarServer = 'Development'
        branch = 'CRI-025171-Code_Breakers-12022018'
        branch = env.BRANCH_NAME
        //branch = branch.substring(branch.indexOf('/')+1)
        echo "Branch ID: ${branch}"
    }

    // stage('Checkout') {
    //     checkout scm
    // }

  stage('Sonar') {

    def scannerHome = tool 'DefaultSonarRuner_2.4'
     
    withSonarQubeEnv(sonarServer) {
      bat "${scannerHome}/bin/sonar-runner -Dsonar.branch=" + branch    
    }

  }
  stage('Compile') {
       bat 'C:/Users/kugaldes/AppData/Roaming/npm/lessc ../PruebaBLUE@script/WebContent/bel-main-style.less ../PruebaBLUE@script/WebContent/bel-main-style.css'  
    }
}


