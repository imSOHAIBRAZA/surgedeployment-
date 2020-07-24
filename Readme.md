1.	Npm install –g surge
2.	Surge token
3.	Surge

For create secrete key global variable 

1.	Setting -> Secrets 
2.	Name and add surge token value 

Surge Deployment  Using github actions CI/CD :
1.	 First deploy code on github repo
2.	After create secrete key variable 
3.	Click on actions
4.	Clcik on set up a workflow yourself 
name: Continuous Deployment
	on: [push]
	
	jobs:
	    deploy:
	        runs-on: ubuntu-latest
	        steps:
	            - uses: actions/checkout@v2
	            
	            - run: echo "Setting up NodeJs"
	            - name: Setup NodeJs
	              uses: actions/setup-node@v1
	              with:
	               node-version: 12.x
	
	            - run: npm install -g surge
	            - run: echo "Deploying website"
	            - run: surge ./ ${{ secrets.SURGE_DOMAIN }} --token ${{ secrets.SURGE_TOKEN }} 
	          
	            - run: echo "Please visit => ${{ secrets.SURGE_DOMAIN }}"

