SELinux policy for allowing container applications (container_t) read/write access to files while allowing an uncontainerized server (httpd_t) to read them.

Ensure necessary packages are installed (Alma 9 specific example)
`sudo dnf install policycoreutils policycoreutils-python-utils selinux-policy selinux-policy-devel`

Run compile from directory
`make -f /usr/share/selinux/devel/Makefile`

Install Policy
`sudo semodule -i container_shared_httpd_content.pp`

Temporarily label for testing
`chcon -R -t container_shared_httpd_content_t /target/path`

Permanently add label
`semanage fcontext -a -t container_shared_httpd_content_t "/target/path(/.*)?"`


