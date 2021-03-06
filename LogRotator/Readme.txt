﻿LogRotator read configuration for LogRotator.xml file, it must be present in same directory.

Sample of LogRotator.xml configuration file
<logRotator poolInterval="900000">
  <!--
  poolInterval: Interval between files search based on following patterns  
  
  === Pattern element specifications ===  
  
  action: determine file should be compressed or delete from system file, rotate action will first compressed the file and delete the original file
  
  dirPath: Directory to search for matching files
  
  filePattern: (*.log) Glob file pattern for files to rotate or delete
  
  offset:  Files older than this duration will selected. Hint: (Now - dateOffset)
              Note: File modified date is the system timestamp of file last modification date
              Format: [d.]hh:mm:ss, e.g. 1 hour = 01:00:00, 1 day = 1.00:00:00
              Optional
  
  deleteUnCompressed: Must be set for file not ending .gz extension (only used in delete action)
  
  subDirs: (true|false) If true search subdirectories for files matching files under dirPath. Use with precautions. Optional

  minSize: if the log file's size in bytes is less than this specified amount the log rotator skips the file. Optional
        
  -->
  <pattern action="rotate" dirPath="Logs" filePattern="*.log" offset="00:01:00" subDirs="true"/>
  <pattern action="delete" dirPath="Logs" filePattern="*.gz" offset="00:10:00" deleteUnCompressed="false" subDirs="true" minSize="100000"/>
</logRotator>