# YandexWeather
Docker image with swagger API v3.0 to Yandex Weather API 
This is an open Docker image  of a Docker Container with swagger API Doc to Yandex Weather API 
if you install it you can use it as a doc to make an integration to yandex Weather open API

THe link to my Docker Hub repo is: https://hub.docker.com/layers/ottonturkg/weatherapidoc_10122022/Weather5/images/sha256-ba048532d2c9ec1e4a6560c9ab380ec22c30b55352a1b1fb2cbe429a6acf7c4a?context=repo
The link to yandex Weather Doc is: https://yandex.ru/dev/weather/doc/dg/concepts/forecast-test.html (test access)
You also need to genarate API KEY from developer mode: https://developer.tech.yandex.ru/?from=commercial
You also need to have a Yandex id to work with its API

How I created this Docker image with Swagger:
(you may take swagger doc from here: https://swagger.io/docs/open-source-tools/swagger-editor/)
0. you need to install Docker from https://docs.docker.com/
1.You need to install gitbash and have a git account repository   (https://github.com/)
2. Download from https://github.com/swagger-api/swagger-editor to local machine ( yours) and unzip it
3. Download and install NodeJS from https://nodejs.org/en/
4. then Open with admin mode gitBash tool and make a command: 
$ cd ..
$ cd ..
goto NodeJS folder previousely downloaded and make a command in gitbush: 

    $ npm install;

5. Go to Swagger-editor folder folder with previousely downloaded from https://github.com/swagger-api/swagger-editor
in Bush make a command: 
cd ..
cd ..
cd  swagger-editor-master

6.Install docker image with swagger editor locally from your machine
in  git bash make a command:
  $ git clone https://github.com/swagger-api/swagger-editor.git
  $ cd swagger-editor
  $ npm install
  $ npm run build
  $ npm start
 7. You also may install docker image with swagger API to Docker with gitbush command (not making point 6):
   docker pull swaggerapi/swagger-editor
   docker run -p 80:8080 swaggerapi/swagger-editor
 8. GOTO Docker desctop and find in tree "images" your installed "swaggerapi/swagger-editor": 
   
 9. here you should press RUN button and open setting page where you need to fill in:
 9.1 Container Name: <WEATHER 5>  --your name
 9.2 Ports: 80  --your port
 9.3 Container Path:  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin   --your local path
 9.4 press start  
 
 10. GoTO Containers/Apps in Docker desctop and find you container Weather5 and turn it on if it is still OFF
 here you should open weblink to Swagger editor on your localhost (currently  it will be on http://localhost/
 11. Here make you swagger interface with YAML language and save it
 
 12. Create you image from container:
    find all containers on host: 
    $ docker ps -a;
  find something like: 
  39 hours ago        Up 2 hours                  0.0.0.0:80->80/tcp, 8080/tcp   Weather5 b0eea3b52d17   swaggerapi/swagger-editor:latest               "/docker-entrypoin
 13. start container it it is not turned on:
    $ docker start Weather5
    
 14. $ docker commit Weather5
 see result like:  sha256:7d4e256a50092e70a7d95d0bdab453e8af298beb03faba473fe3c583719b6658
 15. See all saved images:
 $ docker images -a
 and find you latest. Save it imageid for futhour
 16. give a tag name for future image: 
 $ docker tag 7d4e256a5009 weather5_image  (with you image id!)
 
 17. See new allocated to taged image name for container:
$ docker images -a 
resul like: weather5_image   latest  7d4e256a5009   6 minutes ago 
18 . Create you own image from a container with allocated tagged name: 
$ docker commit Weather5 weather5_image
result like:  sha256:17e56565cd71e4bf6dcad8605682a4136a298e5262b9852bdf707b15eb57aea5

19. Check result of new image: $ docker images -a:
result like: 
        weather5_image  latest   17e56565cd71   56 seconds ago   61.5MB
!!!!!Check the same in Docker Desctop in Images tree ( it should appear weather5_image there!!!!!)
20.  Send Docker new image to DockerHub repo @ottonturkg/weatherapidoc_10122022:    

$ docker tag weather5_image ottonturkg/weatherapidoc_10122022:YandexWeather
$ docker push ottonturkg/weatherapidoc_10122022:YandexWeather

21. You may check that your new image contain updated swagger API for Yandex Weather :
GOTO Images and RUN weather5_image:
give name to container: Weather5_image 
give a 80 to PORTS: 80
give a path to container:  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

22. Conntect to GitHub:
xxxx

