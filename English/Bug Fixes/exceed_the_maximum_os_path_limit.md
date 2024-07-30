# How to Enable Long File Names in Windows 10 


Starting with Windows 10 version 1803, you can support file names up to 32,767 characters long, a significant improvement over the previous 260-character limit. To take advantage of this functionality, you need to enable support for long paths. Here's how to do it: 

# 1 - Option 1: Via Group Policy (GPO) 
  * Open the Group Policy Editor: 
  
  * Press Win + R to open the Run dialog box.
  * Type gpedit.msc and press Enter.
  * Navigate to the required setting:
  
  * Go to Computer Configuration > Administrative Templates > System > File System.
  * Enable long path support: 
  
  * Find and double-click the Enable NTFS long paths policy.
  * Select Enabled and click OK.
  * Restart your computer for the changes to take effect.

# 2 - Option 2: Via Registry Editor 
  * Launch Registry Editor: 
  
  * Press Win + R to open the Run dialog box.
  * Type regedit and press Enter.
  * Navigate to the registry key: 
  
  * Go to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem.
  * Modify the value of LongPathsEnabled:
  
  * Double-click LongPathsEnabled.
  * Set the value to 1 and click OK.
  * Restart the computer to apply the changes