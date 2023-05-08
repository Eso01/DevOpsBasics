        pipeline{
            tools{
                jdk 'java'
                maven 'mymaven'
            }
            agent none
            stages{
                stage('Checkout'){
                    agent any
                    steps{
                echo 'cloning...'
                        git 'https://github.com/Eso01/DevopsBasics.git'
                    }
                }
                stage('Compile'){
                    agent {label 'slave2'}
                    steps{
                        echo 'compiling...'
                        sh 'mvn compile'
                }
                }
                stage('CodeReview'){
                    agent {label 'slave1'}
                    steps{
                    
                echo 'codeReview...'
                        sh 'mvn pmd:pmd'
                    }
                }
               
                stage('Package'){
                    agent any
                    steps{
                        sh 'mvn package'
                    }
                }
            }
        }
