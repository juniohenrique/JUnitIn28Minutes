#!/usr/bin/env groovy

import groovy.json.JsonOutput

def slackNotificationChannel = 'poc-jenkins'     // ex: = "builds"

def notifySlack(text, channel, attachments) {
    def slackURL = 'https://hooks.slack.com/services/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'
    def jenkinsIcon = 'https://wiki.jenkins-ci.org/download/attachments/2916393/logo.png'

    def payload = JsonOutput.toJson([text: text,
        channel: channel,
        username: "Jenkins",
        icon_url: jenkinsIcon,
        attachments: attachments
    ])

    sh "curl -X POST --data-urlencode \'payload=${payload}\' ${slackURL}"
}

node {
    stage("Post to Slack") {
        notifySlack("Success!", slackNotificationChannel, [])
    }
}