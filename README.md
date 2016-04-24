# gitlab-ee-subgit

Image: [marq/gitlab-ee-subgit](https://hub.docker.com/r/marq/gitlab-ee-subgit/)

[GitLab](http://gitlab.org)'s Enterprise Edition, with [SubGit](http://www.subgit.com) v3.1.2 installed.

All of [GitLab's Docker-related documentation](http://doc.gitlab.com/omnibus/docker/) remains valid; the only difference compared to the [official Docker image(s)](https://hub.docker.com/r/gitlab/gitlab-ce/) provided by GitLabHQ is that this image contains an installation of SubGit, a tool for migrating and even mirroring subversion and git source code repositories. In addition, one more volume (`/etc/subgit`) is exposed, allowing to store SubGit related  things like a license key.

[Subgit's SVN to Gitlab Howto](http://www.subgit.com/gitlab.html) is a worthwhile read.

## Volumes

`/etc/gitlab`: Configuration of the GitLab server

`/var/opt/gitlab`: Repositories

`/var/log/gitlab`: Logfiles

`/etc/subgit`: Location for subgit.key (if available; SubGit will find it there)

`/etc/cron.d`: Location for cron jobs (e.g., backups; see below)

## Usage

For GitLab itself, see http://doc.gitlab.com/omnibus/docker/.

For SubGit and Gitlab, see http://www.subgit.com/gitlab.html.

In contrast to the original image, the cron daemon is also launched when starting up GitLab. This allows processing of cron jobs added to /etc/cron.d. 

## Tags

Note that the tag `:latest` is automatically build from the official GitLab repository; whenever GitlabHQ decides to push a new (even experimental) image. I handle versioned tags manually, based on officially tagged images as available in the Official GitLab repository. Should I forget to update, please raise a ticket at github. Thanks!

## SubGit Versions

Starting with the image for v8.7 of GitLab, the SubGit included in this image is at v3.1.2. For a while, I'll be maintaining an alternate image with the older v3.0.0 of SubGit included. The images can be distinguished by their tags, e.g.:

    gitlab-ee-subgit:8.7.0-ee.0: GitLab v8.7.0 (EE), SubGit v3.1.2
    gitlab-ee-subgit:8.7.0-ee.0-3.0.0: GitLab v8.7.0 (EE), SubGit v3.0.0
    
The `:latest` image is also using SubGit v3.1.2.

## Related

Bertrand Roussel provides at standalone Docker image ([corfr/subgit](https://registry.hub.docker.com/u/corfr/subgit/) | [Github](https://github.com/CoRfr/docker-subgit)) for an alternative approach to use SubGit with (in fact any) dockerized git repository servers.

If you are looking for a Docker image combining GitLab's Community Edition (CE) with SubGit, please check out [marq/gitlab-ce-subgit](https://hub.docker.com/r/marq/gitlab-ce-subgit/).