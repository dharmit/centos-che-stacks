Introduction
============

This repo contains `stacks.json` that one can append to existing file with same
name in order to get additional stacks for use in Eclipse Che IDE.

How to add custom stacks to Eclipse Che?
========================================

TL;DR: Append the contents of `stacks.json` to existing `stacks.json` file
created by Eclipse Che.

Follow below instructions for details on how to start Eclipse Che and append
the `stacks.json` file to it.

- Start Eclipse Che with the help of eclipse/che Docker image:

    ```
    $ docker run --rm -t -v /var/run/docker.sock:/var/run/docker.sock eclipse/che start
    ```

- Above command would create a new user called `user` and place Che related
  files under /home/user/che directory.

- If you don't see files there, try restarting or stopping the eclipse/che
  container.

- `stacks.json` can be found under `/home/user/che/storage/stacks.json`.
  Append `stacks.json` in this repo to that file.

-  Now start Eclipse Che with the codenvy/che-server Docker image:

    ```
    $ docker run --net=host \                                             
           --name che \
           -v /var/run/docker.sock:/var/run/docker.sock \
           -v /home/user/che/lib:/home/user/che/lib-copy \
           -v /home/user/che/workspaces:/home/user/che/workspaces \
           -v /home/user/che/storage:/home/user/che/storage \
           codenvy/che-server
    ```

- Hit [http://localhost:8080](http://localhost:8080) in your browser and you
  should see the Eclipse Che IDE running. There won't be any
  projects/workspaces in their yet.

- Click on "Workspaces" in the navigation pane on the left. Click on "+" icon
  at top-right of the screen.

- Under "Select Stack" section, click on "Stack Library". You should see the
  custom stacks that you created.
