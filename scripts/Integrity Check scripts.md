###### **Checking whether the Post-migration ran and was saved successfully. If it returns “True” then it was successful.**

Test-Path "C:\\Users\\olly\\Desktop\\post\_migration\_hashes.csv"



**Comparing Pre and Post migration hashes**

$pre = Import-Csv "C:\\Users\\olly\\Desktop\\pre\_migration\_hashes.csv"

$post = Import-Csv "C:\\Users\\olly\\Desktop\\post\_migration\_hashes.csv"

$comparison = Compare-Object $pre $post -Property Hash, Path

if ($comparison -eq $null -or $comparison.Count -eq 0) {

&#x20;   Write-Host "100% DATA INTEGRITY CONFIRMED - All hashes match" -ForegroundColor Green

} else {

&#x20;   Write-Host "DISCREPANCIES FOUND - Data integrity compromised" -ForegroundColor Red

&#x20;   $comparison

}



