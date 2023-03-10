# Run Amazon Linux 2 Locally on Docker

To test Amazon Linux 2 locally, you can start with the [official AWS Amazon Linux 2 image](https://hub.docker.com/_/amazonlinux/). In spite of that, that image is a slim image and does not include all the tools that are available on an EC2 when running Amazon Linux 2 AMI.

To install all the tools that are available on Amazon Linux 2 AMI:

​yum groupinstall ami


