Capstone=production
KeyJenkinsSSH=jenkins
ParameterValue=production
region=us-east-2
artifactsBucket=artifacts-bucket-ruben
prefix=ruben
profile=ruben
certarn=arn:aws:acm:us-east-2:407889348041:certificate/b9105bd8-0e7f-4555-817a-d2b76fe81c05
hostedzoneid=Z16NEDU5AVPKX2

deploy:
	# aws cloudformation deploy \
	# --template-file capstone-user.yaml \
    # --stack-name $(prefix)-user \
	# --capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND CAPABILITY_NAMED_IAM \
	# --profile $(profile) \
	# --region $(region) \
	# --parameter-override \
	# Capstone=$(Capstone) \
	# KeyJenkinsSSH=$(KeyJenkinsSSH) \

	# aws cloudformation deploy \
	# --template-file capstone-network.yaml \
    # --stack-name $(prefix)-network \
	# --capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND CAPABILITY_NAMED_IAM \
	# --profile $(profile) \
	# --region $(region) \
	# --parameter-override \
	# Capstone=$(Capstone) \
	# KeyJenkinsSSH=$(KeyJenkinsSSH) \

	# aws cloudformation deploy \
	# --template-file capstone-eks.yaml \
    # --stack-name $(prefix)-eks \
	# --capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND CAPABILITY_NAMED_IAM \
	# --profile $(profile) \
	# --region $(region) \
	# --parameter-override \
	# Capstone=$(Capstone) \
	# KeyName=$(KeyJenkinsSSH) \

	aws cloudformation deploy \
	--template-file capstone-jenkins.yaml \
    --stack-name $(prefix)-jenkins \
	--capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND CAPABILITY_NAMED_IAM \
	--profile $(profile) \
	--region $(region) \
	--parameter-override \
	Capstone=$(Capstone) \
	KeyJenkinsSSH=$(KeyJenkinsSSH) \

	

