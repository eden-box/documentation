# Eden Box Documentation

## Description
These documents summarize all knowledge needed in order to redeploy and maintain the existing Eden Box project components, while requiring only basic Linux and sysadmin knowledge, easily acquirable online.

## Outline
The project relies upon two Ubuntu virtual machines, both provided by [Okeanos-Global](./services/okeanos.md).
Both machines automatically update daily at 6 a.m WEST, using unattended-upgrades utility.
Additionally, machines create a snapshot of their current state twice a month (1st and 15th) and upload it to Okeanos [Pithos](./services/okeanos.md#pithos) service, providing recoverability means in case of severe failure of the VMs.
Given that Pithos' capacity is limited, these snapshots overwrite older ones so that, at a given time, only 2 distinct snapshots of a machine are stored in the cloud.

The machine with the role of file server, designated from here on as _eden-fs_, provides:
- Nextcloud service, the file storage platform;
- Public interface to Nextcloud;
- Python application, requests file access entries of Nextcloud log and sends them to the database.

The machine with database role, designated from here on as _eden-db_, provides:
- PostgreSQL database, saves the timestamps of each file accessed on the server
<!--* TODO add Data Science capabilities information -->

For more information about the machines, please refer to [machines](./services/machines.md) section.

Each admin member can access the machines through ssh authentication, solemnly to their own user.
These required RSA keys are ad-hoc distributed to each user.
The key used to authentication a user is the same on both machines, which allows easier configuration at the expense of a more resilient security solution.
Although less pratical to manage, the safest option would require a key pair per-user for each machine.

## Deployment
More information is available on the [deployment](./deployment/) section. 

## Maintenance
Even though many maintenance steps have been suppressed through automation, there are still some tasks that require administrative attention and support. 
Please refer to the [maintenance](./maintenance/) section for more information.

## Security Concerns
Up to the available knowledge at the time of deployment, the best practices and concerns related to Cyber-security have been attended. However, the system's resilience to miscreants still relies on the most vulnerable link: its users. Therefore, extreme care is advised to admin users whilst handling private keys and database user certificates, as those possessing them are implicitly provided access to machines and therefore able to undermine the system at will. Hence, under any circumstance should admin users grant access to third parties whose trust is not assured.

## License
All documentation in this repository is licensed under the Creative Commons Attribution 4.0 International license ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)).

## Acknowledgments
All collaboration and commitment of those involved in this project is truly cherished and appreciated.

_"It must be considered that there is nothing more difficult to carry out nor more doubtful of success nor more dangerous to handle than to initiate a new order of things."_ - Machiavelli
