# 1.Git Work Flow
I forked the repo as instructed and cloned into my local machine. I then created client docker file and server docker file which i then pushed to docker hub. I created a docker compose which would be used to run all the three components at the  same time.

# 2.Images used
The three images below were created and but only client and backend image were pushed to docker hub

matagaro12/yoloclient_ip2 
matagaro12/yolobackend_ip2 
Mongo

The image sizes of matagaro12/yoloclient_ip2  was 244MB while matagaro12/yolobackend_ip2  was 143MB. Initially they  were over 800MBS combined total but after reducing the number of layers in each individual docker file, the sizes came down.

Unfortunately the size of mongo image was well over 600MB as there was no  more optimaziation that could have taken place.

The two images matagaro12/yoloclient_ip2  and matagaro12/yolobackend_ip2 were versioned to 1.0.3 and 1.0.1  respectively following the smever conventions. The versions were increased due to the need to optimise image sizes hence more verions were created.

Below are the screenshot url links to the images deployed on dockerhub
 ![IP2_Docker_client_image](https://github.com/Thazes/yolo/blob/master/dockerhubimages/yolo_client_docker_image.png" IP2_Docker_client_image")

  ![IP2_Docker_backend_image](https://github.com/Thazes/yolo/blob/master/dockerhubimages/yolo_backend_docker_image.png" IP2_Docker_backend_image")

# 3.Image Deployment
The matagaro12/yoloclient_ip2 image and matagaro12/yolobackend_ip2 image were tagged with my username to enable upload to my Docker Hub repository. Mongo image was not tagged with my username and pushed to Docker Hub since the docker-compose file pulls it direclty from Docker Hub during running of the application.

# 4.Service Orchestration
Three containers below were successfully created and run using docker-compose file

Once the docker-compose file is run it starts the database container which in turn triggers the backend container to start which in turn triggers the client container to run. The backend app waits for the database to start and then connects to it before allowing the frontend app to connect to the backend which connects it to the database.

I created a custom bridge yolo-network and put the three containers all in the network. The IP addresses were automatically assigned to the individual services.
