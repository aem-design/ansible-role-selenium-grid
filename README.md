# Ansible Role: Selenium Grid

[![Build Status](https://travis-ci.org/aem-design/ansible-role-selenium-grid.svg?branch=master)](https://travis-ci.org/aem-design/ansible-role-selenium-grid)

Setup Selenium Grid to test your services.
> This role was developed as part of
> [AEM.Design](http://aem.design/)

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

| Name                            	| Required 	| Default                                                           	| Notes                            	|
|---------------------------------	|----------	|-------------------------------------------------------------------	|----------------------------------	|
| docker_image_user               	|          	| selenium                                                          	|                                  	|
| docker_image_name               	|          	| hub                                                               	|                                  	|
| docker_image                    	|          	| {{ docker_image_user }}/{{ docker_image_name }}                   	|                                  	|
| docker_image_tag                	|          	| latest                                                            	|                                  	|
| docker_timezone                 	|          	| Australia/Melbourne                                               	|                                  	|
|                                 	|          	|                                                                   	|                                  	|
| service_selenium_grid_timeout   	|          	| 10                                                                	|                                  	|
| service_selenium_grid_name      	|          	| selenium-grid                                                     	|                                  	|
| service_selenium_grid_http_port 	|          	| 4444                                                              	|                                  	|
| service_selenium_grid_host      	|          	| localhost                                                         	|                                  	|
|                                 	|          	|                                                                   	|                                  	|
| docker_container_name           	|          	| {{ service_selenium_grid_name | default('selenium-grid') }}       	|                                  	|
| docker_published_ports          	|          	|                                                                   	|                                  	|
|                                 	|          	| - "0.0.0.0:{{ service_selenium_grid_http_port }}:4444/tcp"        	|                                  	|
|                                 	|          	|                                                                   	|                                  	|
| wait_delay                      	|          	| 1                                                                 	| how long to wait between retries 	|

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - { role: aem_design.selenium_grid
    }
```

## License

Apache 2.0

## Author Information

This role was created by [Max Barrass](https://aem.design/).