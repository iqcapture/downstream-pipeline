# downstream-pipeline
CloudBees Core trial walk-thru

Registering event triggers as instructed,  fail:

		// downstream-pipeline
		pipeline {
			agent any

			-- cannot update in CloudBees Ops Center...
			-- get: Invalid trigger type "eventTrigger". Valid types: [upstream, cron, snapshotDependencies, githubPush, pollSCM]
			-- using "upstream" produces build error: No such DSL method 'simpleMatch' found
			triggers {
				eventTrigger(simpleMatch("testingCompleted"))
			}
			stages {
				stage('Received an event') {
					steps {
						echo 'I just received a testingCompleted event'
					}
				}
			}
		}
