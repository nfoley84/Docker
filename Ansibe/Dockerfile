FROM ubuntu:18.04

RUN apt update -y && \
    apt install python3.3 python3-dev gcc libpng-dev g++ build-essential libssl-dev libffi-dev curl wget -y

RUN apt install python3-pip  libpython2.7-stdlib -y && \
    apt install python-pip -y && \
    pip3 install wheel && \
    pip3 install --upgrade setuptools

RUN apt-get update -y && \
    apt upgrade -y

RUN apt update && \
    apt install -y software-properties-common && \
    rm -rf /var/lib/apt/lists/*

RUN apt-add-repository ppa:ansible/ansible -y && \
    apt-get update -y && \
    apt install ansible -y

RUN pip3 install pyvmomi &&\
    pip3 install requests-credssp && \
    pip3 install pywinrm && \
    pip3 install pywinrm[credssp] && \
    pip install pyvmomi &&\
    pip install requests-credssp && \
    pip install pywinrm && \
    pip install pywinrm[credssp]

RUN apt install python3-pip libpython2.7-stdlib install python-pip -y && \
    unmask 022 && \ 
    pip3 install -r requirements.txt
    
RUN apt-get update && \
    apt-get upgrade -y && \
    apt install git -y && \
    apt install openssh-server -y && \
    mkdir -p /var/run/sshd && \
    apt install openjdk-8-jdk -y && \
    apt install maven -y && \
    adduser --quiet ansible && \
    echo "ansible:ansible" | chpasswd && \
    mkdir /home/ansible/.m2

RUN apt-get install -y wget apt-transport-https
RUN wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN apt update 
RUN apt install software-properties-common 
RUN add-apt-repository 'deb http://security.ubuntu.com/ubuntu xenial-security main'
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
RUN apt update
RUN apt install libicu55 -y
RUN pip3 instal requests
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
RUN apt-get update -y 
RUN ACCEPT_EULA=Y apt-get install msodbcsql17 -y
RUN ACCEPT_EULA=Y apt-get install mssql-tools -y 
RUN echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile 
RUN echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
RUN apt-get install unixodbc-dev -y
RUN pip3 install --upgrade pyodbc
RUN pip3 install ldap3 
RUN pip install wheel
RUN pip install --upgrade setuptools
RUN pip install requests
RUN pip install --upgrade py

RUN ansible-galaxy collection install community.vmware -f
RUN ansible-galaxy collection install dellemc.openmanage -f
RUN ansible-galaxy collection install ansible.windows -f 
RUN ansible-galaxy install azure.aks -f 
RUN ansible-galaxy install azure.azure_modules -f 
RUN ansible-galaxy collection install servicenow.servicenow -f 
RUN ansible-galaxy collection install vmware.vmware_rest -f 
RUN service ssh start

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
