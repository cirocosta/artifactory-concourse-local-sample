WHAT

	an example artifactory + concourse docker-compose setup for testing purposes



REQUIREMENTS

	1. docker + docker-compose
	2. artifactory pro license (you can get a 30day trial from jfrog)


USAGE

	bring concourse and artifactory pro up

		docker-compose up -d


	map `127.0.0.1` to the virtual repository


		127.0.0.1 artifactory docker.artifactory


	go the the UI (http://localhost) and create a docker repository


	verify that `login` works:

		docker login docker.artifactory
			user=admin
			password=password


	set the concourse pipeline
		
		fly -t local --concourse-url http://localhost:8080 -u test -p test
		fly -t local set-pipeline -p test -c ./pipeline.yml


	let it run

		fly -t local unpause-pipeline -p test


	go to the UI and see it working.
