# Example Setup for ClamSAP on SLESxx

VSI in context of SAP stands for Virus Scan Inferface, see https://launchpad.support.sap.com/#/notes/817623 

# Howto start
First install a VSI compatible product. What it that? In gernal it is a standard AV product with an add-on for SAP. The add-on is shared library. SAP processes are able to perform on-demand AV scans with this add-on. The add-on is called Virus Scan Adapter. This is the name of the shared library. This overview provides a list of possible integrations: https://launchpad.support.sap.com/#/notes/1494278

## VSI test tool
ftp://ftp.sap.com/pub/icc/nw-vsi/VSA-SDK-2.0.zip

## Run the report
You can execute se38 or sa38 to execute zvsisetup. You need to import the VSA_LIB. VSA_LIB is the path and name to a Virus Scan Adapter.
Example: You have installed clamd + clamsap (https://sourceforge.net/projects/clamsap/). The VSA name is libclamdsap.so, which its default location is /usr/local/lib/libclamdsap.so. Therefore enter /usr/local/lib/libclamdsap.so in the input field VSA_LIB.
Finally execute the report (or press F8).

## Re-run the report
After the setup the report switches to the standard configuration view of VSI. This standard view can also be started with transaction VSCAN. If you execute the report a second time, then you directly see VSCAN, because this report is only to demonstrate the setup. You are free to modify the source of zvsisetup to change this behaviour.

# Adapter only
Please remark: This report will only setup an adapter into the ABAP process. The installation of a remote RFC server (called Virus Scan Server) is not integrated.

