node {
    stage ('checkout') {
        checkout scm
        dir('pipeline-helper') {
            checkout scm: [$class: 'GitSCM'
                , branches: [[name: '*/master']]
                , userRemoteConfigs: [
                    [credentialsId: '1c126120-7f08-4bfb-b869-81ddde1a5354', url: 'git@bitbucket.org:bumblebeeee/pipeline-helper.git']
                ]
            ]
        }
    }
    stage ('test') {
        def molecule = docker.build('molecule', './molecule-image')
        molecule.inside('-v /var/run/docker.sock:/var/run/docker.sock') { c ->
            sh '''
                molecule test
            '''
        }
    }
}











//node('ansible') {
//    //if master tag (get maximum tag #)and push back
//    stage("Checkout") {
//        checkout scm
//    }
//
//    stage("Test") {
//
//
//        //docker.image("quay.io/ansible/molecule:3.0.3").inside(
//        //    '-u root -v /var/run/docker.sock:/var/run/docker.sock -v $PWD:/var/myrole') { c ->
//        //    sh "cd /var/myrole && molecule test"
//        //}
//    }
//    if (env.BRANCH_NAME.equals("master")) {
//        echo "create tag && push tag back"
//    } else if (env.BRANCH_NAME.equals("develop")) {
//        echo env.BRANCH_NAME
//    } else if (env.BRANCH_NAME.startsWith("feature")){
//        echo env.BRANCH_NAME
//    }
//
//}
//pipeline {
//  agent {
//    docker {
//      image 'dr1s/molecule-ubuntu'
//      args '-v /var/run/docker.sock:/var/run/docker.sock'
//    }
//  }
//
//  stages {
//
//    stage ('Display versions') {
//      steps {
//        sh '''
//          docker -v
//          python -V
//          ansible --version
//          molecule --version
//        '''
//      }
//    }
//
//    stage ('Molecule test') {
//      steps {
//        sh 'molecule test --all'
//      }
//    }
//
//  } // close stages
//}   // close pipeline
//
