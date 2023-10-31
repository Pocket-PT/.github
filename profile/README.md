# Pocket PT
English | **한국어**

# 소개

온라인 PT를 원활하게 
채팅과 영상 및 사진으로 PT 피드백을 진행하고, 대시보드에서 회원을 편리하게 관리할 수 있는 서비스<br>
자세한 설명은 <a href="https://github.com/Pocket-PT/.github/blob/main/profile/POCKET%20PT_compressed.pdf">여기</a>를 클릭


# System Architecture
<!-- <img width="1168" alt="스크린샷 2023-08-11 17 54 51" src="https://github.com/Pocket-PT/.github/assets/59956020/9317fcf2-53ad-4735-8e56-56fc49c77c56"> -->
![image](https://github.com/Pocket-PT/.github/assets/55998816/d5dbd5d7-b004-49eb-82ab-fa9212074ac8)



# Tech Stack
## **:zap: Tech Stack**
```
- Frontend: Gatsby, React, typescript
- Backend: Java 17, Spring Boot, Spring Security, JPA, OAuth2 Client, JWT, Websocket, STOMP
- Database: MySQL
- Version control: Git, Github
- CI/CD: Github Actions, SonarQube, Docker Compose, AWS
- Monitoring tool: ELK, Google Analytics
- API Document: Postman
- IDE: Visual studio code, IntelliJ
- Team Collaboration Tool: Notion, Jira, Confluence
```
|Frontend|Backend|DevOps|IDE|Team Collaboration Tool|
|:------:|:------:|:----:|:---:|:---:|
|![Gatsby](https://img.shields.io/badge/gatsby-663399?style=for-the-badge&logo=gatsby&logoColor=black)<br>![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)<br>![TypeScript](https://img.shields.io/badge/typescript-3178C6?style=for-the-badge&logo=typescript&logoColor=black)|![Java17](https://img.shields.io/badge/java-orange.svg?style=for-the-badge&logo=java&logoColor=white)<br>![SpringBoot](https://img.shields.io/badge/SpringBoot-6DB33F.svg?style=for-the-badge&logo=SpringBoot&logoColor=white)<br>![MySQL](https://img.shields.io/badge/MySQL-4479A1.svg?style=for-the-badge&logo=MySQL&logoColor=white)<br>|![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)<br>![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)<br>![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)<br>![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)<br>![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)<br>|![Visual Studio Code](https://img.shields.io/badge/VisualStudioCode-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)<br>![IntelliJ](https://img.shields.io/badge/IntelliJ-000000.svg?style=for-the-badge&logo=intellij-idea&logoColor=white)<br>|![Jira](https://img.shields.io/badge/Jira-0052CC.svg?style=for-the-badge&logo=jira&logoColor=white)<br>![Confluence](https://img.shields.io/badge/Confluence-172B4D.svg?style=for-the-badge&logo=confluence&logoColor=white)<br>![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=Postman&logoColor=white)<br>![Notion](https://img.shields.io/badge/Notion-%23000000.svg?style=for-the-badge&logo=notion&logoColor=white)

# Installation
## 서버 환경 실행
  - Execution: Dev Mode
    1. 실행 버전
      실행은 Release tag의 v1.0.0에서 진행합니다.
    2. 실행 환경
      도커 환경에서 실행되도록 만든 개발환경입니다.
      아래 내용을 실행하기 전, 도커 deamon이 local 환경에 세팅되어 있는지 확인해주세요.

  - Run command
    ```
    cd “YOUR_DOWNLOAD_LOCATION”
    
    git clone https://github.com/Pocket-PT/backend-repo
    
    ## insert configFile (.env.dev)
    vi .env.dev
    
    ## Before starting the next line, update .env.dev using the information below.
    docker-compose -f docker-compose.dev.yml up --build
    
    ```

  - .env.dev
    ```
    # Spring setting
    SPRING_PROFILES_ACTIVE=dev
    SPRING_JPA_GENERATE_DDL=true
    SPRING_JPA_HIBERNATE_DDL_AUTO=create
    
    # Database setting for docker
    MYSQL_DATABASE=userdb
    MYSQL_ROOT_HOST=root
    MYSQL_ROOT_PASSWORD=rootpwd
    
    # Spring Database setting for docker
    SPRING_DATASOURCE_URL=jdbc:mysql://mysql-db:3306/userdb?useSSL=false&autoReconnect=true&allowPublicKeyRetrieval=true&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC
    SPRING_DATASOURCE_USERNAME=root
    SPRING_DATASOURCE_PASSWORD=rootpwd
    
    # Spring OAuth setting
    SPRING_SECURITY_KAKAO_CLIENT_ID=${YOUR_SPRING_SECURITY_KAKAO_CLIENT_ID}
    SPRING_SECURITY_KAKAO_CLIENT_SECRET=${YOUR_SPRING_SECURITY_KAKAO_CLIENT_SECRET}
    SPRING_SECURITY_KAKAO_REDIRECT_URI=http://localhost:8080/login/oauth2/code/kakao
    
    # Spring JWT setting
    JWT_SECRET=${YOUR_JWT_SECRET}
    # 24시간(ms)
    JWT_ACCESS_EXPIRATION=60
    # JWT_ACCESS_EXPIRATION=86400000
    # JWT_ACCESS_EXPIRATION=20000
    # 1주일(ms)
    JWT_REFRESH_EXPIRATION=604800000
    JWT_HEADER=Authorization
    JWT_PREFIX=Bearer
    
    # Spring CORS setting
    # CORS_FRONTEND=https://pocketpt.netlify.app
    CORS_FRONTEND=http://localhost:8080/api/v1/main
    
    # Spring AWS S3 setting
    AWS_S3_BUCKET_NAME=${YOUR_AWS_S3_BUCKET_NAME}
    AWS_S3_BUCKET_URL=${YOUR_AWS_S3_BUCKET_URL}
    AWS_S3_REGION=${YOUR_AWS_S3_REGION}
    AWS_S3_ACCESS_KEY=${YOUR_AWS_S3_ACCESS_KEY}
    AWS_S3_SECRET_KEY=${YOUR_AWS_S3_SECRET_KEY}
    
    # Spring Redis setting for docker
    SPRING_REDIS_HOST=redis
    SPRING_REDIS_PORT=6379
    SPRING_REDIS_PASSWORD=${YOUR_SPRING_REDIS_PASSWORD}
    
    ```

## 프론트 환경 실행
  ```
  cd “YOUR_DOWNLOAD_LOCATION”

  git clone https://github.com/Pocket-PT/frontend-repo
  
  npm i

  npm run dev
  ```


# Feature
![ezgif com-optimize (2)](https://github.com/Pocket-PT/.github/assets/59956020/14e2b733-c260-402c-9659-710f13d3ad5b)
![pocket pt](https://github.com/Pocket-PT/.github/assets/59956020/ea831869-3886-4e60-8a6d-129f957eb22d)
<br><br>

# Team Member

|Name|김산|김일곤|박수현|
|:---:|:---:|:---:|:---:|
| Role    |   PM, Backend, DevOps   |    Frontend, DevOps     | Backend, DevOps |
| Github  | [@san](https://github.com/kimtks456) | [@ilgon](https://github.com/ilgon0110) | [@vivian0304](https://github.com/vivian0304) |
