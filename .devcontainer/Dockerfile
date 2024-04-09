FROM node:18

# install git
RUN apt update 
RUN apt install git


ARG DEBIAN_FRONTEND=noninteractive

ENV BING_HEADER ""

# Set home to the user's home directory
ENV HOME=/home/user \
	PATH=/home/user/.local/bin:$PATH

# Set up a new user named "user" with user ID 1000
RUN useradd -o -u 1000 user && mkdir -p $HOME/app && chown -R user $HOME

# Switch to the "user" user
USER user

WORKDIR $HOME/app


RUN git clone https://github.com/renqabs/bg.git bg
RUN chown -R user $HOME/app/bg
WORKDIR $HOME/app/bg
RUN npm install
RUN npm run build

ENV PORT 8080
EXPOSE 8080
