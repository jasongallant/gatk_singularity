################################################################################
# Basic bootstrap definition to build CentOS 7 container from Docker container
################################################################################

BootStrap: docker
From: broadinstitute/gatk

################################################################################
# Copy any necessary files into the container
################################################################################

################################################################################
# Install additional login shells for users that need them
################################################################################

################################################################################
# Install additional packages
################################################################################

################################################################################
# Create directories to enable access to common HPCC mount points
################################################################################
sudo mkdir -p /mnt/home
sudo mkdir -p /mnt/research
sudo mkdir -p /mnt/dfs17
sudo mkdir -p /mnt/ffs17
sudo mkdir -p /mnt/local
sudo mkdir -p /mnt/ls15
sudo mkdir -p /opt/software

################################################################################
# Run the user's login shell, or a user specified command
################################################################################
%runscript
SHELL="$(getent passwd $USER | awk -F: '{print $NF}')"
SHELL=${SHELL:-/bin/bash}
if [[ "$@" == "" ]]; then
  exec env -i TERM="$TERM" HOME="$HOME" $SHELL -l
else
  exec env -i TERM="$TERM" HOME="$HOME" $@
fi
