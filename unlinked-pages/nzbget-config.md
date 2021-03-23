# NZBGet-Config.md

work in progress

## SECURITY

* To setup a login:
  1. Set a "ControlUsername" and "ControlPassword".
  2. Set an "AddUsername" and "AddPassword" to protect API access.
  3. Select "Form Auth" to `Yes`
  4. Click "Save" and then "Reload".

## DOWNLOAD QUEUE

* DiskSpace: `250000` \(or your preference\)
  * Will prevent NZBGet from filling up your drive.
  * 250GB is a generous amount to leave for other tasks \(e.g. extractions, backups, etc\).

## CHECK AND REPAIR

* HealthCheck: `Delete`
  * Will keep your intermediate folder from filling up with unrepairable downloads. 

