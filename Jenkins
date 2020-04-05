pipeline{
agent {label 'devserver1'}
stages{
stage('1'){
steps{
checkout([$class: 'GitSCM', 
    branches: [[name: '*/master']], 
    userRemoteConfigs: [[credentialsId: '303ea41d-0f53-49b1-a745-ae9a2ca3c1c7', url: 'https://github.com/praveenpenugonda/mavenrepo.git']]
])

}
}

stage('build'){
steps{
sh 'mvn package'

}
}

stage('sonar'){
steps{
withSonarQubeEnv('sonar'){
sh "mvn sonar:sonar"
}


}
}

stage('tomcat'){
steps{
sh 'scp /root/workspace/samplejob/target/studentapp-2.5-SNAPSHOT.war 15.206.74.173:/var/lib/tomcat/webapps'

}
}


}
}
