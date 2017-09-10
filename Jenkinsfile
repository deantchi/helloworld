#!/usr/bin/env groovy

import hudson.model.*
import hudson.EnvVars
import groovy.json.JsonSlurperClassic
import groovy.json.JsonBuilder
import groovy.json.JsonOutput
import java.net.URL

//name of local artifactory server
def server = Artifactory.server 'local_artifactory'

version = null

//defines artifactory repo
def artifactory_repo = 'helloworld'

boolean is_master = ("${env.BRANCH_NAME}" == "master")

    //specify node to build on
	node('builder-bob') {

	try {
			stage('Clean workspace') {
				deleteDir()
				sh 'ls -lah'
			}

			stage('Checkout SCM') {
				checkout scm
			}

	String archive_dir = "output"
	String output_dir = "helloworld/${archive_dir}/${getVersion()}/files/"

			stage('Archive File') {
				dir(archive_dir) {
					archiveArtifacts "**"

          //defines artifactory upload spec
          def uploadSpec = """{
            "files": [
              {
                "pattern": "**",
                "target": "${version}/"
              }
           ]
          }"""
          server.upload(uploadSpec)
				}
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
