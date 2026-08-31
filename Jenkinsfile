pipeline{
    agent any
    stages{
        stage('Run Postman Scenarios'){
           steps{
bat'''
@echo off
for /d %%S in (run\\*) do (
             echo
==========================================================
              echo Running Scenario:%%S
              echo
===========================================================

for  %%C in ("%%S\\*.postman_collection.json") do (
set COLLECTION=%%C
)

for  %%E in ("%%S\\*.postman_environment.json") do (
set ENVIRONMENT=%%E
)
                if exist "%%S\\data.json"(
                newman run "!COLLECTION!" -e "!ENVIRONMENT!" -d "%%S\\data.json" -r html --reporter-html-extra "report.html"
                )else (
                newman run "!COLLECTION!" -e "!ENVIRONMENT!" -r html --reporter-html-extra "report.html"
                )
                )
                '''
           }
        }
    }
}
   
     




