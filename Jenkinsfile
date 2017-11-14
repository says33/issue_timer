pipeline {
  agent any

    stages {
      stage('Build') {
        steps {
          checkout scm
           // sh "MIX_ENV=test mix deps.get"

        }
      }
      stage('log') {
        steps {
          sh '''previous_tag=0
            tagLog='git log'
            tagPretty="--pretty=format:'*  %s [View](https://bitbucket.org/projects/test/repos/my-project/commits/%H)'"
            for current_tag in $(git log --pretty=format:"%h")
              do
                if [ "$previous_tag" != 0 ];then
                  tag_date=$(git log -1 --pretty=format:'%ad' --date=short ${previous_tag})
                    printf "## ${previous_tag} (${tag_date})\n\n"
                    ${tagLog} ${current_tag}...${previous_tag} ${tagPretty} --reverse | grep -v Merge
                    printf "\n\n"
                fi
                previous_tag=${current_tag}
              done >>  index3.html'''


          publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '.', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: 'index3.html'])
        }
      }
   }
}
