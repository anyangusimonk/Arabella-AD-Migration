###### **Creating the folder Structure**

$base = "C:\\AraballaShare"

$folders = @(

&#x20;   "$base\\Credit",

&#x20;   "$base\\IT",

&#x20;   "$base\\Customer Relations",

&#x20;   "$base\\Finance and Procurement",

&#x20;   "$base\\Sales and Marketing"

)

foreach ($folder in $folders) {

&#x20;   New-Item -ItemType Directory -Path $folder -Force

}



##### **Creating AD Security groups**

###### **Creating the Groups’ OU**

New-ADOrganizationalUnit -Name "Groups" -Path "DC=arabellainc,DC=local"

Creating the groups

New-ADGroup -Name "GRP\_Credit" -GroupScope Global -GroupCategory Security -Path "OU=Groups,DC=arabellainc,DC=local"

New-ADGroup -Name "GRP\_IT" -GroupScope Global -GroupCategory Security -Path "OU=Groups,DC=arabellainc,DC=local"

New-ADGroup -Name "GRP\_CustomerRelations" -GroupScope Global -GroupCategory Security -Path "OU=Groups,DC=arabellainc,DC=local"

New-ADGroup -Name "GRP\_FinanceProcurement" -GroupScope Global -GroupCategory Security -Path "OU=Groups,DC=arabellainc,DC=local"

New-ADGroup -Name "GRP\_SalesMarketing" -GroupScope Global -GroupCategory Security -Path "OU=Groups,DC=arabellainc,DC=local"	









###### **Creating Domain Users**

$password = ConvertTo-SecureString "{Arabella\*}@2025" -AsPlainText -Force



New-ADUser -Name "Wanda Aima" -GivenName "Wanda" -Surname "Aima" -SamAccountName "walma" -UserPrincipalName "walma@arabellainc.local" -Path "CN=Users,DC=arabellainc,DC=local" -AccountPassword $password -Enabled $true



New-ADUser -Name "Maggy Awish" -GivenName "Maggy" -Surname "Awish" -SamAccountName "mawish" -UserPrincipalName "mawish@arabellainc.local" -Path "CN=Users,DC=arabellainc,DC=local" -AccountPassword $password -Enabled $true



New-ADUser -Name "Nate Olwen" -GivenName "Nate" -Surname "C" -SamAccountName "Olwen" -UserPrincipalName "nolwen@arabellainc.local" -Path "CN=Users,DC=arabellainc,DC=local" -AccountPassword $password -Enabled $true



New-ADUser -Name "John Mikel" -GivenName "John" -Surname "Mikel" -SamAccountName "jmikel" -UserPrincipalName "jmikel@arabellainc.local" -Path "CN=Users,DC=arabellainc,DC=local" -AccountPassword $password -Enabled $true



New-ADUser -Name "Tim Mash" -GivenName "Tim" -Surname "Mash" -SamAccountName "tmash" -UserPrincipalName "tmash@arabellainc.local" -Path "CN=Users,DC=arabellainc,DC=local" -AccountPassword $password -Enabled $true





###### **Assigning users to groups in-line with their respective departments**

Add-ADGroupMember -Identity "GRP\_Credit" -Members "walma"

Add-ADGroupMember -Identity "GRP\_IT" -Members "nolwen"

Add-ADGroupMember -Identity "GRP\_CustomerRelations" -Members "mawish"

Add-ADGroupMember -Identity "GRP\_FinanceProcurement" -Members "Tmash"

Add-ADGroupMember -Identity "GRP\_SalesMarketing" -Members "jmikel"



