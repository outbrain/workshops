FROM ubuntu
RUN apt-get update
# JSON format for the install command
RUN ["apt-get", "install", "figlet"]
# Always do this:
ENTRYPOINT ["figlet", "-f", "script"]
# If user does not provide a command, use this one
CMD hello default

