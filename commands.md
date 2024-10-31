- docker network create deo-network
- docker build -t deo-actions-runner -f .\.infrastructure\deo-actions-runner.Dockerfile .\.infrastructure\
- docker run --name deo-actions-runner -ti --network deo-network deo-actions-runner:latest
    - ./config.sh --url https://github.com/stadler-pascal/deo-webapp --token ARRBKGLACDZ3MOSPSXXL7ULHA7WPA
        - No args  
    - ./run.sh
     - STRG + P, STRG + Q -- to detach

 - docker run -d --name deo-sonarqube --network deo-network --restart unless-stopped -p 9000:9000 sonarqube:10.7.0-community

Sonar password: DEO!admin123
Sonar token: sqp_d04480cd8eca579b308b0286a5beb0006c9b1a28
New: sqp_67bf7eb9cfa394f347e068d1f7e393819c0f0dc0
Sonar key: Deo.WebApp
Sonar Host: http://deo-sonarqube:9000