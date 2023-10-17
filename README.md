# Why
I thought that [renovatebot](https://renovatebot.com) is able to update docker dependencies inside [ansible](https://www.ansible.com/) documents but this hasn't worked for me. After some reasearch I figured out the [ansible manager](https://docs.renovatebot.com/modules/manager/ansible/) will only work for files under the /tasks/ directory. 

Maybe I was only not able to get this running with renovate defaults but I have spend round about a day into this topic and maybe this repo can save someone some time. Lets get started!


# basic structure
I have simpliefied everything, this is not a directly runable example, but you should get the conenction between everything.

The docker dependency for renovate is configured in [group_vars/all/vars.yaml](/group_vars/all/vars.yaml) -> renovate_image
The variable is used inside the [docker-compose.yml.j2](/roles/renovate/templates/docker-compose.yml.j2) Jinja template.
Renovates config is [config.js.j2](/roles/renovate/templates/config.js.j2) 
The config is added inside docker-compose as a volume and both files should be placed on the server e.g. with ansible, this part is not implemented here.

# regexmanager
the regemanager is located inside the [config.js.j2](/roles/renovate/templates/config.js.j2)
### Important notice:
- double escape the backslash (\) 
- I have created an example on regex101 where you can test this regex https://regex101.com/r/Co0lfU/1
- If something is not working set logFileLevel: "debug" and look into the logfile, this doesn'T have to be the docker log check your logile config



