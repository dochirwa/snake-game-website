node('appserver')
{
  def app

  stage('Cloning Git')
  {
    checkout scm
  }        
  stage('Build-and-Tag')
  {
    app = docker.build("dchirwa/snakegame-website:latest")
  }  
  stage('SAST-SNYK')
  {
    echo "test"
  }      
  stage('Post-to-DockerHub')
  {
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials')
    {
      app.push("latest")
    }
  }        
  stage('Pull-Image-Server')
  {
    sh "docker-compose down"
    sh "docker-compose up -d"
  }
        
}