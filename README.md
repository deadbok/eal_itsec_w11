# EAL - IT security - Week 11 #

Files for IT security Week 11 at Erhvervsakademiet Lillebealt.

## Work pack A - SSH ##

 * SSH
 * SSH keys
 * SSH tunnel
 * Jump host: a proxy to access the internal network using SSH.

## Work pack B - Packer ##

The goal is to make a virtual machine image with Debian and XFCE. This
is done using packer and a template as well as the supplied ansible role
that install an XFCE environment on a Debian system.

Packer is an open source tool for creating identical machine images for
multiple platforms from a single source configuration.

### Packer flow ###

 * Download external ISO images
 * Create an HTTP server to serve files to the VM
 * Create VM
 * Create virtual HD
 * Boot the VM and serve `preseed.cfg` for unattended installation
    * `pressed.cfg` Sets up a basic Debian system with an SSH server and  ansible
 * Copy files for provisioning onto the machine using SSH
 * Run the ansible provisioning on the VM


### Ansible role ###

The ansible role that install XFCE is here:

[https://github.com/deadbok/ansible-role-workstation-xfce4](https://github.com/deadbok/ansible-role-workstation-xfce4)

### Ansible and Packer guides ###

[https://www.azavea.com/blog/2014/10/09/creating-ansible-roles-from-scratch-part-1/](https://www.azavea.com/blog/2014/10/09/creating-ansible-roles-from-scratch-part-1/)

[http://blog.endpoint.com/2014/03/provisioning-development-environment.html](http://blog.endpoint.com/2014/03/provisioning-development-environment.html)

### Ansible docs ###

[https://www.packer.io/docs/](https://www.packer.io/docs/)

## CIS 3 ##

###  CSC 3: Secure Configurations for Hardware and Software ###

 |Family  | CSC | Control Description                                   | Foundational | Advanced |
 |:-------|:---:|:------------------------------------------------------|:-------------|:---------|
 | System | 3.1 | Establish standard secure configurations of operating systems and software applications. Standardized images should represent hardened versions of the underlying operating system and the applications installed on the system. These images should be validated and refreshed on a regular basis to update their security configuration in light of recent vulnerabilities and attack vectors. | Y | File integrity of master images are verified as part of a continuous monitoring program. |
 | System | 3.2 | Follow strict configuration management, building a secure image that is used to build all new systems that are deployed in the enterprise. Any existing system that becomes compromised should be re-imaged with the secure build. Regular updates or exceptions to this image should be integrated into the organization’s change management processes. Images should be created for workstations, servers, and other system types used by the organization. | y | |
 | System | 3.4 | Perform all remote administration of servers, workstation, network devices, and similar equipment over secure channels. Protocols such as telnet, VNC, RDP, or others that do not actively support strong encryption should only be used if they are performed over a secondary encryption channel, such as SSL, TLS or IPSEC. | Y | |
 | System | 3.5 | Use file integrity checking tools to ensure that critical system files (including sensitive system and application executables, libraries, and configurations) have not been altered. The reporting system should: have the ability to account for routine and expected changes; highlight and alert on unusual or unexpected alterations; show the history of configuration changes over time and identify who made the change (including the original logged-in account in the event of a user ID switch, such as with the su or sudo command). These integrity checks should identify suspicious system alterations such as: owner and permissions changes to files or directories; the use of alternate data streams which could be used to hide malicious activities; and the introduction of extra files into key system areas (which could indicate malicious payloads left by attackers or additional files inappropriately added during batch distribution processes). | Y | File integrity of critical system files are verified as part of a continuous monitoring program. |
 | System | 3.6 | Implement and test an automated configuration monitoring system that verifies all remotely testable secure configuration elements, and alerts when unauthorized changes occur. This includes detecting new listening ports, new administrative users, changes to group and local policy objects (where applicable), and new services running on a system. Whenever possible use tools compliant with the Security Content Automation Protocol (SCAP) in order to streamline reporting and integration. | Y |  |
 | System | 3.7 | Deploy system configuration management tools, such as Active Directory Group Policy Objects for Microsoft Windows systems or Puppet for UNIX systems that will automatically enforce and redeploy configuration settings to systems at regularly  scheduled intervals. They should be capable of triggering redeployment of configuration settings on a scheduled, manual, or event-driven basis. | Y | |

#### CSC 3 Procedures and Tools ####

Rather than start from scratch developing a security baseline for each
software system, organizations should start from publicly developed,
vetted, and supported security benchmarks,security guides, or
checklists. Excellent resources include:

 * The Center for Internet Security Benchmarks Program [www.cisecurity.org](www.cisecurity.org)
 * The NIST National Checklist Program [checklists.nist.gov](checklists.nist.gov)

Document any change or deviation from these guides.
