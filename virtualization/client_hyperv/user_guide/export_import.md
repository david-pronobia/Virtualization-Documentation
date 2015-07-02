ms.ContentId: 040B1B51-0F25-4295-B317-8CC4DE0A1AFF
title: Export and import virtual machines

# Exporting and Importing virtual machines #

You can use the export and import functionality to quickly duplicate virtual machines or to move them from one host to another.

## Export ##


You don't need to export a virtual machine in order to be able to import it. But, the export functionality exists and it can be an easy way to prepare virtual machines to be imported.

For information about using Windows PowerShell to export virtual machines, see [Export-VM](https://technet.microsoft.com/library/hh848491.aspx)


1. In Hyper-V Manager, right-click the virtual machine and select **Export**.
2. Click **Browse** in the dialog box and choose where you would like to put the exported VM and then click **Select Folder**. 
3. In the **Export Virtual Machine** dialog, click **Export**.


## Import ##

You don't need to export a virtual machine to be able to import it. You can simply copy a virtual machine and its associated files to the new host, and then use the **Import Virtual Machine** wizard to specify the location of the files. This registers the virtual machine with Hyper-V and makes it available to be used. 

In addition to the wizard, the Hyper-V module for Windows PowerShell includes cmdlets for importing virtual machines. For more information, see [Import-VM](https://technet.microsoft.com/library/hh848495.aspx).

1. In **Hyper-V Manager**, in the **Action** menu, click **Import Virtual Machine**.
2. In the Locate Folder section, click Browse and navigate to where the virtual machine files. Click **Next** when finished.
3. Select the virtual machine to import and then click **Next**.
4. In the Choose Import Type section, you can choose how to import the virtual machine:


    | **Import type** | **Description** |
    |:-----|:-----|
    | **Register** | Uses the existing unique ID of the virtual machine and registers it in-place. Choose this option if the virtual machines files are already in the correct location. |
    | **Restore** | Uses the original virtual machine’s unique ID and also copies the virtual machine files to the default location specified for the host. |
    | **Copy** | Creates a new unique ID for the virtual machine and also copies the virtual machine files to the default location specified for the host. |


5. After selecting how to import the VM, click **Next**.
6. In the Choose Destination section, you can choose where to store the files for the virtual machine or leave them in their current location. When you are finished, click **Next**.
7. In Choose Storage folders, you can select another place to store the .vhdx file or leave them where they are. When you are finished, click **Next**.
8. When you have finished importing the VM, you will see the summary page describing where the new VM files are located.



The Import Virtual Machine wizard also walks you through the steps of addressing incompatibilities when you import the virtual machine to the new host—so this wizard can help with configuration that is associated with physical hardware, such as memory, virtual switches, and virtual processors. To import a virtual machine, the wizard does the following:

1. Creates a copy of the virtual machine configuration file. This is done as a precaution in case an unexpected restart occurs on the host, such as from a power outage.
2. Validates hardware. Information in the virtual machine configuration file is compared to hardware on the new host.
3. Compiles a list of errors. This list identifies what needs to be reconfigured and determines which pages appear next in the wizard. 
4. Displays the relevant pages, one category at a time. The wizard explains each incompatibility to help you reconfigure the virtual machine so it is compatible with the new host. 
5. Removes the copy of the configuration file. After the wizard does this, the virtual machine is ready to be started.
