stage 'Dev'
node {
    checkout scm
    sh "MIX_ENV=test mix deps.get"
    sh "MIX_ENV=test mix compile"
}

stage 'QA'
node {
    echo "Testing ${env.BRANCH_NAME}..."
    sh "mix test"
}
