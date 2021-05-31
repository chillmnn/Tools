### Search Examples
* msf> search EternalBlue type:exploit—find every exploit that refers to EternalBlue.
* msf> search platform:"Windows XP SP3" type:exploit -o /root/xpsp3_exploits.csv—find every exploit that applies to Windows XP SP3 and save to xpsp3_exploits.csv.
* msf> search Windows/VNC type:payload—find every VNC payload that applies to Windows.
* msf> search Windows/MSSQL type:exploit—find every exploit that can be used against Microsoft SQL running on Windows.
* msf> search Windows/SMB type:exploit -S great—find all Windows-based SMB exploits that have an excellent (most reliable) ranking (have the string "excellent" in the row results).
* msf> search scanner/smb—search for every scanner that has to do with SMB.
* msf> search scanner/mssql—search for every scanner that has to do with Microsoft SQL.
