pipeline {
    //agent {
    //    label "java-8"
    //}
    stages  {
       // stage('Preparation') {
            //steps {
              //git 'https://github.com/bg7nyt/java.git'
            //}
        //}
        //stage('Build') {
            //steps {
            //sh "mvn -Dmaven.test.failure.ignore clean package"
            //archive 'target/*.jar'
            //}
        //}
        
        stage("Label"){
            steps {
            setBuildStatus("Build complete", "SUCCESS");
            }
        }
        
        //stage('Results') {
            //steps {
            //sh 'mvn test'
            //junit '**/target/surefire-reports/*.xml'
            //}
      
        //}
    }
}

void setBuildStatus(String message, String state) {
  step([
      $class: "GitHubCommitStatusSetter",
      reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/bg7nyt/java.git"],
      contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
      errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
  ]);
}
