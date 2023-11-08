pipeline{
    agent {label 'RAppsDesktop11'}
    parameters {
        choice(name: "Portal", choices: ['RappsLnx1100Pt'])
    }

    environment {
        PWD = pwd()
    }
    stages{
        stage("Build"){
            steps{
                git branch: 'main', credentialsId: 'd1e86ef9-07a6-461b-b8c7-4805e9572662', url: 'https://github.com/resosro/Insights-Desktop-Pipeline'
                echo "branch pulled"
                sh "${PWD}\\Insights-Desktop-Pipeline\\scripts\\build.ps1"
            }
        }
        stage("Test"){
            steps{
                git branch: 'main', credentialsId: 'd28f4340-67ba-48ac-a47d-810f37cf684c', url: 'https://devtopia.esri.com/Release/Insights-DesktopAutomation'
                sh "${PWD}\\Powershell-Scripts\\test.ps1"
            }

        }

        stage("Clean"){
            steps{
                sh "${PWD}\\Powershell-Scripts\\clean.ps1"

            }
        }
    }
}