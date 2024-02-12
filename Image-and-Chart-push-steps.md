# Steps to build and push Image or Chart to private repo

### Steps to Docker build and push Image to DockerHub private repo:

Once you are ready with your changes - 

Run **git tag** command from root directory

First, please check the previous tag and use the incremental version of that.
Create git tag in local

```shell
git tag v4.5.6-d1
```
Push the tag to the remote repo

```shell
git push origin v4.5.6-d1
```
It will trigger the **TMDC Docker Image CI workflow** github action pipeline.
**grafana** docker image will be built with the **TAG** and pushed to DOCKER HUB private repo **rubiklabs**


### Steps to Chart Push to our ECR:

Once you are ready with your changes - 

Run **git tag** command from root directory

First, please check the previous tag and use the incremental version of that.
Create git tag in local

```shell
git tag 4.5.6-d1
```
Push the tag to the remote repo

```shell
git push origin 4.5.6-d1
```
It will trigger the **TMDC Helm Push CI workflow** github action pipeline.
**grafana** chart will be built with the **TAG** and pushed to our ecr.


**NOTE:** 

1.  KEEP IN MIND !!!
        FOR **IMAGE TAG** START TAG WITH **"v"**

2.  Always maintain the semantic version (major.minor.patch) fixed and provide a suffix **-d** with it.
    Tag will be incremental like ```shell major.minor.patch-d(+1 increment)```

    ex ```shell 4.5.6-d1, 4.5.6-d2, 4.5.6-d3 ... ``` like that

    We can update and push the **major.minor.patch** section of the tag once there is a release of docker image with official repo with same major/minor/patch version and also if we merge the changes to our repo.

    ex: Lets say 4.5.6 or 4.7.5 image version released . Once changes have been merged to our repo we will use tag 4.5.6-d(+1) or 4.7.5-d(+1).  
