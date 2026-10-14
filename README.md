> ```
    Project deployment in Instance 
    Step 1:
        Configure database
        apt install mysql-server -y
        mysql_secure_installation
        mysql -uroot -p
        >> create user linux identified by "Redhat";
        >> grant all privileges on *.* to linux;
        >> flush privileges;
        >> create database flightdb;
        >> exit
    
     Step2:
        Deploy Backend:
         cd Flight-reservation
         cd FlightReservationSystem
         apt install openjdk-17-jdk -y
         apt install maven -y
         #Configure Creds of DB
         vim application.properties
           Add database creds
         cp -rvf application.properties ./src/main/resources/
   
     Step3:
         cd frontend/
         apt install nodejs npm -y
         ls -a
         vim .env
           add Backend URL
         npm install
         npm run build
         apt install apache2 -y
         cp -rvf dist/* /var/www/html/
         systemctl start apache2
     
   
     Step 4:
       mvn clean package
       cd target/
       java -jar flightreservationApplication-0.0.1-SNAPSHOT.jar
     
    
```
