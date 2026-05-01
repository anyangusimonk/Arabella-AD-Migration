###### **Generating a Pre-migration hash and storing a CSV file on a desktop**

Get-ChildItem -Path "C:\\Users\\olly\\Desktop\\AraballaData" -Recurse -File |

Get-FileHash -Algorithm SHA256 |

Export-Csv -Path "C:\\Users\\olly\\Desktop\\pre\_migration\_hashes.csv" –NoTypeInformation



###### 

###### **Generating a Post-migration hash and storing a CSV file on a desktop**

Get-ChildItem -Path "C:\\Users\\olly\\Desktop\\Arabella Data 2026" -Recurse -File |

Get-FileHash -Algorithm SHA256 |

Export-Csv -Path "C:\\Users\\olly\\Desktop\\post\_migration\_hashes.csv" –NoTypeInformation



