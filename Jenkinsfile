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
            for current_tag in $(git log --pretty=format:"%h")
              do
                if [ "$previous_tag" != 0 ];then
                  tag_date=$(git log -1 --pretty=format:'%ad' --date=short ${previous_tag})
                    printf "## ${previous_tag} (${tag_date})\n\n"
                    git log ${current_tag}...${previous_tag} --pretty=format:'*  %s [View](https://bitbucket.org/projects/test/repos/my-project/commits/%H)' --reverse | grep -v Merge
                    printf "\n\n"
                fi
                previous_tag=${current_tag}
              done >>  index3.html'''



           publishHTML target: [
                allowMissing: false,
                alwaysLinkToLastBuild: false,
                keepAll: true,
                reportDir: ".",
                reportFiles: 'index3.html',
                reportName: 'HTML gitlog'
           ]
        }
      }
   }
}
