#!/usr/bin/env groovy

import hudson.model.*
import hudson.EnvVars
import groovy.json.JsonSlurperClassic
import groovy.json.JsonBuilder
import groovy.json.JsonOutput
import java.net.URL

//name of local artifactory server
artifactserver = Artifactory.server 'local_artifactory'

version = null

//defines artifactory repo
def artifactory_repo = 'helloworld'

//booleen is_master ( "${env.BRANCH_NAME}" == "master")

    //speficy node to build on
	node('builder-bob') {

	try {
			stage('Clean workspace') {
				deleteDir()
				sh 'ls -lah'
			}

			stage('Checkout SCM') {
				checkout scm
			}

			stage('Building') {
			}
	}

	catch (e) {
		throw e
	}

	finally {

	}
}



//fetches "Version_File", read, and pulls version number
String getVersion() {
	if (!version) {
		version = readFile('VERSION_FILE').replaceAll(/[\n\r]/, '')
		}
	return version
}
