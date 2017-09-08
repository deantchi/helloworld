#!/usr/bin/env groovy

import hudson.model.*
import hudson.EnvVars
import groovy.json.JsonSlurperClassic
import groovy.json.JsonBuilder
import groovy.json.JsonOutput
import java.net.URL

version = null
def emailto = 'deantchi@gmail.com'


//defines artifactory
//def artifactory_repo = ''

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
				string getVersion()
				if (!version) {
					version = readFile('VERSION').replace(/[\n\r]/, '')
				}
			}
	}

	catch (e) {
		throw e
	}

	finally {

	}
}
