pipeline{
    agent any
    stages{
        stage('Run Postman Collections'){
           steps{
bat'''
@echo off

             echo
==========================================================
              echo Running Postman Collections
              echo
===========================================================

for /r %%C in (*.postman_collection.json) do (
                 echo.
                 echo Collection:%%C
   
        if not exist "%%~dpC*.postman_environment.json"(
                              echo ERROR:
     Environment file not found
                          exit /b 1
)
                   for %%E in("%%~dpC*.postman_environment.json") do (
        echo 
   Environment: %%E

                           if exist"%%~dpCdata.json"(
                        echo Data file found 
                        echo Running with data file...

   newman run "%%C" -e "%%E"
)
    if errorlevel1(
echo Newman execution failed 
    exit /b 1
)
)
)


              echo,
              echo
=====================================================================
               echo All Collections Completed
               echo
======================================================================
'''
}
}
}
}



    
}
