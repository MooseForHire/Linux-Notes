
### What is a Dockerfile?

A text file written in a specific format, which has instructions and arguments that Docker can understand.

Example:

```
FROM node
Or
RUN npm install
Or
FROM ubuntu
```

Instructions are written on the left side (in caps). Everything to the right-hand side is an argument.

The "From" instruction basically pulls in an OS or an existing Image, for example - FROM ubuntu will give us access to ubuntu commands (apt-get update).

The "RUN" command instructs docker to run a particular command on the image in which you are creating. These are pulled in the "FROM" command.

Example:

```
FROM ubuntu

RUN apt-get uppdate
RUN apt-get install node
RUN npm install
```
