# Docker compose

Docker Compose is a tool for running multi-container applications. 
A `docker-compose.yaml` file is used to define how one or more containers 
that make up your application are configured, such as:

```yml
version: '3.4'

services:
  restsvr:
    image: imageName
    ports:
      - 443:8000      # HOST / CONTAINER
    build:
      context: .
      dockerfile: ./Dockerfile

    logging:
      driver: "json-file"
      options:
        max-size: "100m"
        max-file: "5"
```

At the project root, you can create and start your application with:

```sh
docker-compose up --build -d
```

the flag `-d` stands for deamon, which is good for production. While
If you want to see the logs on the terminal avoid the deamonization.

<!--  Script to show the footer   -->
<html>
<script
    src="https://code.jquery.com/jquery-3.3.1.js"
    integrity="sha256-2Kok7MbOyxpgUVvAk/HJ2jigOSYS2auK4Pfzbm7uH60="
    crossorigin="anonymous">
</script>
<script>
$(function(){
  $("#footer").load("../../footers/footer.html");
});
</script>
<body>
<div id="footer"></div>
</body>
</html>
