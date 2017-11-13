pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout scm
                sh "MIX_ENV=test mix deps.get"
               
            }
        }
        stage('changelog') {
            steps {

                  publisher {
                    gitChangelogRecorder {
                      config {
                        fromType("commit")
                        fromReference("")
                        toType("ref")
                        toReference("master")

                        showSummary(true)
                        showSummaryUseTemplateContent(true)
                        showSummaryTemplateContent("""
                <h1> Git Changelog changelog </h1>
                <p>
                Changelog of Git Changelog.
                </p>
                {{#tags}}
                <h2> {{name}} </h2>
                 {{#issues}}
                  {{#hasIssue}}
                   {{#hasLink}}
                <h2> {{name}} <a href="{{link}}">{{issue}}</a> {{title}} </h2>
                   {{/hasLink}}
                   {{^hasLink}}
                <h2> {{name}} {{issue}} {{title}} </h2>
                   {{/hasLink}}
                  {{/hasIssue}}
                  {{^hasIssue}}
                <h2> {{name}} </h2>
                  {{/hasIssue}}
                   {{#commits}}
                <a href="https://github.com/tomasbjerre/git-changelog-lib/commit/{{hash}}">{{hash}}</a> {{authorName}} <i>{{commitTime}}</i>
                <p>
                <h3>{{{messageTitle}}}</h3>
                {{#messageBodyItems}}
                 <li> {{.}}</li> 
                {{/messageBodyItems}}
                </p>
                  {{/commits}}
                 {{/issues}}
                {{/tags}}
                        """)


                        useMediaWiki(true)
                        mediaWikiUseTemplateContent(true)
                        mediaWikiTemplateContent("""
                __NOTOC__
                = Git Changelog changelog =
                Changelog of Git Changelog.
                {{#tags}}
                == {{name}} ==
                 {{#issues}}
                  {{#hasIssue}}
                   {{#hasLink}}
                === {{name}} [{{link}} {{issue}}] {{title}} ===
                   {{/hasLink}}
                   {{^hasLink}}
                === {{name}} {{issue}} {{title}} ===
                   {{/hasLink}}
                  {{/hasIssue}}
                  {{^hasIssue}}
                === {{name}} ===
                  {{/hasIssue}}
                   {{#commits}}
                [https://github.com/tomasbjerre/git-changelog-lib/commit/{{hash}} {{hash}}] {{authorName}} {{commitTime}}
                '''{{{messageTitle}}}'''
                {{#messageBodyItems}}
                 * {{.}} 
                {{/messageBodyItems}}
                  {{/commits}}
                 {{/issues}}
                {{/tags}}
                        """)


                        useGitHub(true)
                        gitHubIssuePattern(null)
                        gitHubToken(null)
                        gitHubApiTokenCredentialsId(null)
                        useGitHubApiTokenCredentials(false)

                        useReadableTagName(true)
                        readableTagName("-([^-]+?)\$")

                        configFile(null)                    
                        createFileTemplateContent(null)
                        createFileTemplateFile(null)
                        createFileUseTemplateContent(false)
                        createFileUseTemplateFile(false)
                        customIssues {}
                        dateFormat("YYYY-MM-dd HH:mm:ss")

                        useGitLab(false)
                        gitLabServer(null)
                        gitLabProjectName(null)
                        gitLabToken(null)
                        ignoreCommitsIfMessageMatches(null)
                        ignoreCommitsWithoutIssue(false)
                        ignoreTagsIfNameMatches(null)
                        jiraIssuePattern(null)
                        jiraPassword(null)
                        jiraServer(null)
                        jiraUsername(null)
                        jiraUsernamePasswordCredentialsId(null)
                        useJiraUsernamePasswordCredentialsId(false)
                        noIssueName(null)
                        showSummaryTemplateFile(null)
                        showSummaryUseTemplateFile(false)
                        subDirectory(null)
                        timeZone(null)
                        untaggedName(null)
                        useConfigFile(false)
                        useFile(false)
                        useIgnoreTagsIfNameMatches(false)
                        useJira(false)
                        useSubDirectory(false)
                        gitLabApiTokenCredentialsId(null)
                        useGitLabApiTokenCredentials(false)


                      }
                    }
                  }
                }
        }
             
       
        // stage('SonarQube analysis') {
          //   steps {
            //    script {
              //        scannerHome = tool 'SonarQube Scanner 2.5'
                //      echo "${scannerHome}"
                //}
      //          withSonarQubeEnv('sonar') {
        //           sh "${scannerHome}/bin/sonar-runner -e"
          //      }
            // }
          //}

    }
}
