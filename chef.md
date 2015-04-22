# Chef

- A resource describes one part of the system and its desired state.
- A `file` is one kind of resource
- Your policy describes `what` state each resource should be in but not `how` to get there.

		file 'aFilename' do
	  		# action :delete
	  		# or
	  		# content 'hello chef'
		end
		
- Resources have actions.  `:delete` is an example of an action
- An action is the process that achieves a particular configuration state.
- Every resource has a default action
- In the example of adding content to a file, we don't need to specify the `create` action because it is the default action.
- Recipes organize resources.
- `package` has the default action of install.

		package 'httpd'
		
		service 'httpd' do
		  action [:start, :enable]
		end
		
		file '/var/www/html/index.html' do
		  content '<html>
		    <body>
		      <h1>Hello World</h1>
		    </body>
		  </html>'
		end
		
- Chef works in the order you specify

## Cookbooks

- `chef generate cookbook whatever`
- `chef generate template webserver index.html`


- `chef-apply` is used to run a single recipe.
- `chef-client --local-mode --runlist cookbook-name` is used to run a cookbook.


## Knife
- `knife bootstrap ADDRESS --ssh-user root --ssh-password PASSWORD --node-name node1 --run-list 'recipe[webserver]' --bootstrap-version 11.12.8
`
- `knife cookbook upload webserver`

## Kitchen

Test a cookbook with `kitchen test -d never`
`kitchen converge`
Login to a box with `kitchen login`
Sudo into a suer with `sudo su - username-here`