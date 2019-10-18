# Ansible Role: Selenium Grid

[![Build Status](https://travis-ci.org/aem-design/ansible-role-selenium-grid.svg?branch=master)](https://travis-ci.org/aem-design/ansible-role-selenium-grid)

Setup Selenium Grid to test your services.
> This role was developed as part of
> [AEM.Design](http://aem.design/)

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

| Name                                    	| Required 	| Default                                                                                                                                                      	| Notes                                                                	|
|-----------------------------------------	|----------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------	|----------------------------------------------------------------------	|
| docker_image_user                       	|          	| selenium                                                                                                                                                     	| docker user for image                                                	|
| docker_image_name                       	|          	| hub                                                                                                                                                          	| docker image name                                                    	|
| docker_image                            	|          	| {{ docker_image_user }}/{{ docker_image_name }}                                                                                                              	| full docker image                                                    	|
| docker_image_tag                        	|          	| latest                                                                                                                                                       	| docker image tag                                                     	|
| docker_timezone                         	|          	| Australia/Melbourne                                                                                                                                          	| timezone                                                             	|
| docker_shm_size                         	|          	| 1g                                                                                                                                                           	| ram to use for instance                                              	|
|                                         	|          	|                                                                                                                                                              	|                                                                      	|
| grid_timeout           	|          	| 10                                                                                                                                                           	| grid timeout                                                         	|
| grid_debug             	|          	| false                                                                                                                                                        	| grid debug mode                                                      	|
| grid_debug_vncport     	|          	| 5999                                                                                                                                                         	| vnc port for monitoring sessions if not headless                     	|
| grid_xvfb              	|          	| false                                                                                                                                                        	| run in headless mode                                                 	|
| grid_http_port         	|          	| 4444                                                                                                                                                         	| port to expose hub on                                                	|
| grid_host              	|          	| 0.0.0.0                                                                                                                                                      	| public address for hub                                               	|
| grid_status_service    	|          	| /wd/hub/status                                                                                                                                               	| status page for hub                                                  	|
| grid_status_schema     	|          	| http                                                                                                                                                         	| hub schema                                                           	|
| grid_status_url        	|          	| {{ grid_status_schema }}://{{ grid_host }}:{{ grid_http_port }}{{ grid_status_service }} 	| url for status                                                       	|
|                                         	|          	|                                                                                                                                                              	|                                                                      	|
| grid_status_capacity   	|          	| Hub has capacity                                                                                                                                             	| status test when hub has capacity                                    	|
| grid_status_nocapacity 	|          	| No spare hub capacity                                                                                                                                        	| status test when hub has no capacity                                 	|
| grid_status_ready      	|          	| ready                                                                                                                                                        	| general test for hub availability                                    	|
| grid_healthcheck       	|          	|                                                                                                                                                              	| health checks for hub                                                	|
| test                                    	|          	| ["CMD", "/opt/bin/check-grid.sh", "--host", "{{ grid_host }}", "--port", "{{ grid_http_port }}"]                           	| ["NONE"]                                                             	|
| interval                                	|          	| 1m30s                                                                                                                                                        	|                                                                      	|
| timeout                                 	|          	| 10s                                                                                                                                                          	|                                                                      	|
| retries                                 	|          	| 3                                                                                                                                                            	|                                                                      	|
| start_period                            	|          	| 30s                                                                                                                                                          	|                                                                      	|
|                                         	|          	|                                                                                                                                                              	|                                                                      	|
| docker_env                              	|          	|                                                                                                                                                              	| environment variables                                                	|
| TZ                                      	|          	| {{ docker_timezone }}                                                                                                                                        	|                                                                      	|
| GRID_DEBUG                              	|          	| {{ grid_debug }}                                                                                                                            	|                                                                      	|
| GRID_TIMEOUT                            	|          	| {{ grid_timeout }}                                                                                                                          	|                                                                      	|
| START_XVFB                              	|          	| {{ grid_xvfb }}                                                                                                                             	|                                                                      	|
|                                         	|          	|                                                                                                                                                              	|                                                                      	|
| docker_container_name                   	|          	| {{ grid_name | default('selenium-grid') }}                                                                                                  	| default container name                                               	|
| docker_published_ports                  	|          	| [                                                                                                                                                            	| default ports                                                        	|
|                                         	|          	| "0.0.0.0:{{ grid_http_port }}:4444/tcp",                                                                                                    	|                                                                      	|
|                                         	|          	| "0.0.0.0:{{ grid_debug_vncport }}:5900/tcp"                                                                                                 	|                                                                      	|
|                                         	|          	| ]                                                                                                                                                            	|                                                                      	|
|                                         	|          	|                                                                                                                                                              	|                                                                      	|
| docker_volumes                          	|          	| [                                                                                                                                                            	| default valums                                                       	|
|                                         	|          	| "/dev/shm:/dev/shm"                                                                                                                                          	|                                                                      	|
|                                         	|          	| ]                                                                                                                                                            	|                                                                      	|
|                                         	|          	|                                                                                                                                                              	|                                                                      	|
| wait_delay                              	|          	| 1                                                                                                                                                            	| how long to wait between retries                                     	|
| docker_host                             	|          	| unix://var/run/docker.sock                                                                                                                                   	| host where to run the docker container for executing pyaem2 commands 	|
|                                         	|          	|                                                                                                                                                              	|                                                                      	|


## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - { 
      role: "aem_design.selenium_grid",
      debug_hide: false
    }
```

## License

Apache 2.0

## Author Information

This role was created by [Max Barrass](https://aem.design/).
