node {
    stage('git checkout'){
        git credentialsId: 'krati', url: 'https://github.com/kratika10rathore/war-test.git'
        
    }
	stage('Code build & test'){
        def mvnHome = tool name: 'Maven' , type: 'maven'
        bat(/"${mvnHome}\bin\mvn" clean package/)   
    } 
	
	stage("Deploy to tomcat"){
        deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://localhost:8084/')], contextPath: 'sample', war: '**/*.war'
    }

}
