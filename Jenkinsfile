pipeline {
  agent any

  environment {
    GIT_REPO = 'https://github.com/Nio4124/html_3_luglio_2025'
    BRANCH = 'main'
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: "${GIT_REPO}"
      }
    }

    stage('Deploy to GitHub Pages') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'github-token', usernameVariable: 'GIT_USER', passwordVariable: 'GIT_TOKEN')]) {
          sh '''
            git config user.name "Nio4124"
            git config user.email "antoniozottola41204@gmail.com"
            git checkout --orphan gh-pages
            git rm -rf .
            cp index.html .
            git add index.html
            git commit -m "Deploy HTML to GitHub Pages"
            git push -f https://${GIT_USER}:${GIT_TOKEN}@github.com/Nio4124/html_3_luglio_2025.git gh-pages
          '''
        }
      }
    }
  }
}
