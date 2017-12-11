pipeline {
    agent any
    stages {
        //定义mvn环境
        def mvnHome = tool 'maven_3.1.1'
        env.PATH = "${mvnHome}/bin:${env.PATH}"
        env.JAVA_HOME = tool 'JDK_1.8'
        
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
                //mvn 测试
                sh "mvn test"
            }
        }

        stage('mvn build') {
            steps {
                //mvn构建
                sh "mvn clean install -Dmaven.test.skip=true"
            }
        }

        stage('deploy') {
            steps {
                //执行部署脚本
                echo "deploy ......"
                echo "deploy ......"
                echo "deploy ......"
            }
        }
    }
}