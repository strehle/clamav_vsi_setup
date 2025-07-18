# Example Setup for ClamSAP on SLES11/12/15

VSI in context of SAP stands for Virus Scan Inferface, see https://launchpad.support.sap.com/#/notes/817623 

# Howto start
First install a VSI compatible product. What does it mean? In gernal it is a standard AV product with an add-on for SAP. The add-on is shared library. SAP processes are able to perform on-demand AV scans with this add-on. The add-on is called Virus Scan Adapter. This is the name of the shared library. This overview provides a list of possible integrations: https://launchpad.support.sap.com/#/notes/1494278
The Virus Scan Adapter for clamav is called ClamSAP. For SLES it is quite easy to setup it, because you simply can install it with OS installer, see:
https://software.opensuse.org/download.html?project=security&package=clamsap

SLES 11.4 commands:
```
zypper addrepo https://download.opensuse.org/repositories/security/SLE_11_SP4/security.repo
zypper refresh
zypper install clamsap
```
SLES 12.4 commands:
```
zypper addrepo https://download.opensuse.org/repositories/security/SLE_12_SP4/security.repo
zypper refresh
zypper install clamsap
```
SLES 15.5 commands:
```
zypper addrepo https://download.opensuse.org/repositories/security/SLE_12_SP5/security.repo
zypper refresh
zypper install clamsap
```
This will automatically install clamav + clamsap
Check with "clamscan" that clamav is installed correctly. If not you need to download the signature files with freshclam.
After the installation you should to "sudo freshclam". This will download the signatures and should help in using the clamav command.

## VSI test tool
You can also use the vsi.jar within this repository.

# Platforms
Supported platforms: **Windows** | **Linux** 

## Run the test tool
# Java command line example
Java command line example
```
java -jar vsi.jar info -V /usr/lib64/libclamsap.so -cfg vsi.properties
```
Java test scan of EICAR, which is included into vsi.jar
```
java -jar vsi.jar scanbytes EICAR
```

You need to import the VSA_LIB. VSA_LIB is the path and name to a Virus Scan Adapter.
Example: You have installed clamd + clamsap (https://sourceforge.net/projects/clamsap/). The VSA name is libclamdsap.so, which its default location is /usr/lib64/libclamsap.so. Therefore enter /usr/lib64/libclamsap.so in the input field VSA_LIB.




