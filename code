###############################
#HP Laser MFP 432 PCL6 #
################################
$PSScriptRoot = Split-Path -Parent -Path $MyInvocation.MyCommand.Definition
$drivername = "HP Laser MFP 432 PCL6"
$portName = "IP_10.170.0.110"
$PortAddress = "10.170.0.110"

###################
#Staging Drivers   #
###################
pnputil /add-driver C:\Drivers\PRINTERS\HP-432fdn\shn3m.inf /install

#######################
#Installing Drivers   #
#######################

Add-PrinterDriver -Name $drivername

##########################################################
#Install Printerport | check if the port already exist   #
##########################################################

$checkPortExists = Get-Printerport -Name $portname -ErrorAction SilentlyContinue
if (-not $checkPortExists) 
{
Add-PrinterPort -name $portName -PrinterHostAddress $PortAddress
}

####################################
#Check if PrinterDriver Exists     #
####################################
$printDriverExists = Get-PrinterDriver -name $DriverName -ErrorAction SilentlyContinue

##################
#Install Printer #
##################

if ($printDriverExists)
{
Add-Printer -Name "ARARA_02" -PortName $portName -DriverName $DriverName
}
else
{
Write-Warning "Printer Driver not installed"
}

SLEEP 360
