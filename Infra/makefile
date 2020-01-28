Capstone=production
KeyJenkinsSSH=jenkins
region=us-east-2

prefix=ruben
profile=ruben


deploy:
	aws cloudformation deploy \
	--template-file capstone-user.yaml \
    --stack-name $(prefix)-user \
	--capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND CAPABILITY_NAMED_IAM \
	--profile $(profile) \
	--region $(region) \
	--parameter-override \
	Capstone=$(Capstone) \
	KeyJenkinsSSH=$(KeyJenkinsSSH) \

	aws cloudformation deploy \
	--template-file capstone-network.yaml \
    --stack-name $(prefix)-network \
	--capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND CAPABILITY_NAMED_IAM \
	--profile $(profile) \
	--region $(region) \
	--parameter-override \
	Capstone=$(Capstone) \
	KeyJenkinsSSH=$(KeyJenkinsSSH) \

	aws cloudformation deploy \
	--template-file capstone-eks.yaml \
    --stack-name $(prefix)-eks \
	--capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND CAPABILITY_NAMED_IAM \
	--profile $(profile) \
	--region $(region) \
	--parameter-override \
	Capstone=$(Capstone) \
	KeyName=$(KeyJenkinsSSH) \

	aws cloudformation deploy \
	--template-file capstone-jenkins.yaml \
    --stack-name $(prefix)-jenkins \
	--capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND CAPABILITY_NAMED_IAM \
	--profile $(profile) \
	--region $(region) \
	--parameter-override \
	Capstone=$(Capstone) \
	KeyJenkinsSSH=$(KeyJenkinsSSH) \

	

