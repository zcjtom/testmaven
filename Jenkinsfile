pipeline {
    agent any
    
    environment {
        M2_HOME = '/var/jenkins_home/support_tool/maven/apache-maven-3.3.9'
    }
    
    stages {
        //定义mvn环境
        // def mvnHome = tool 'maven_3.1.1'
        // env.PATH = "${mvnHome}/bin:${env.PATH}"
        // env.JAVA_HOME = tool 'JDK_1.8'
        
        stage('get clone') {
            steps {
                //check CODE
                checkout([
                    $class : 'GitSCM',
                    branches : [[name : '*/develop']],
                    doGenerateSubmoduleConfigurations : false,
                    extensions : [[$class : 'LocalBranch', localBranch : 'develop']],
                    submoduleCfg : [],
                    userRemoteConfigs : [[
                        credentialsId : '7e12cd4e-4072-47be-8849-73d2fbefa495', 
                        url : 'https://10.10.1.183:8443/CI0/testmaven.git'
                    ]]
                ])
            }
        }

        stage('mvn test') {
            steps {
                withMaven(maven: 'maven_3.3.9') {
                    //mvn 测试
                    sh "mvn test"
                }
            }
        }

        stage('mvn build') {
            steps {
                withMaven(maven: 'maven_3.3.9') {
                    //mvn构建
                    sh "mvn clean install -Dmaven.test.skip=true"
                }
            }
        }

        stage('deploy') {
            steps {
                //执行部署脚本
                echo "deploy ......"
                sh '''
                    echo "deploy1 ......"
                    echo "deploy1 ......"
                    echo "deploy1 ......"
                    echo "deploy1 ......"
                '''
            }
        }
        
    }
    
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}