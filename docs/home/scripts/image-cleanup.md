# Plex Image Cleanup

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/meisnate12/Plex-Image-Cleanup?style=plastic)](https://github.com/meisnate12/Plex-Image-Cleanup/releases)
[![Docker Image Version (latest semver)](https://img.shields.io/docker/v/meisnate12/plex-image-cleanup?label=docker&sort=semver&style=plastic)](https://hub.docker.com/r/meisnate12/plex-image-cleanup)
[![Docker Pulls](https://img.shields.io/docker/pulls/meisnate12/plex-image-cleanup?style=plastic)](https://hub.docker.com/r/meisnate12/plex-image-cleanup)
[![Develop GitHub commits since latest stable release (by SemVer)](https://img.shields.io/github/commits-since/meisnate12/Plex-Image-Cleanup/latest/develop?label=Commits%20in%20Develop&style=plastic)](https://github.com/meisnate12/Plex-Image-Cleanup/tree/develop)

[![Discord](https://img.shields.io/discord/822460010649878528?color=%2300bc8c&label=Discord&style=plastic)](https://discord.gg/NfH6mGFuAB)
[![Reddit](https://img.shields.io/reddit/subreddit-subscribers/PlexMetaManager?color=%2300bc8c&label=r%2FPlexMetaManager&style=plastic)](https://www.reddit.com/r/PlexMetaManager/)
[![Wiki](https://img.shields.io/readthedocs/plex-meta-manager?color=%2300bc8c&style=plastic)](https://metamanager.wiki/en/latest/home/scripts/image-cleanup.html)
[![GitHub Sponsors](https://img.shields.io/github/sponsors/meisnate12?color=%238a2be2&style=plastic)](https://github.com/sponsors/meisnate12)
[![Sponsor or Donate](https://img.shields.io/badge/-Sponsor%2FDonate-blueviolet?style=plastic)](https://github.com/sponsors/meisnate12)

Your Plex folders are growing out of control. You use overlays from [Plex Meta Manager](https://github.com/meisnate12/Plex-Meta-Manager) (PMM) or upload lots of custom art from [Title Card Maker](https://github.com/CollinHeist/TitleCardMaker) (TCM) that you no longer want to use or need to eliminate. You don't want to perform the plex dance if you can avoid it. This script will free up gigs of space....

It can also perform some Plex operations like "empty trash", "clean bundles", and "optimize db". 

Red is deleted, Green is kept because it is the actively selected poster. The other two come standard from PLEX when the posters are retrieved so the script will not touch those either:

Special Thanks to [bullmoose20](https://github.com/bullmoose20) for the original [Plex Bloat Fix](https://github.com/bullmoose20/Plex-Stuff#plex-bloat-fix) (PBF) Script this is based on.

![](dispaly.png)

## Installing Plex Image Cleanup

Generally, Plex Image Cleanup can be installed in one of two ways:

1. Running on a system as a Python script [we will refer to this as a "local" install]
2. Running as a Docker container

GENERALLY SPEAKING, running as a Docker container is simpler, as you won't have to be concerned about installing Python, or support libraries, or any possible system conflicts generated by those actions.

For this reason, it's generally recommended that you install via Docker rather than directly on the host.

If you have some specific reason to avoid Docker, or you prefer running it as a Python script for some particular reason, then this general recommendation is not aimed at you.  It's aimed at someone who doesn't have an existing compelling reason to choose one over the other.

### Install Walkthroughs

There are no detailed walkthroughs specifically for Plex Image Cleanup but the process is extremely similar to how you would do it with [Plex Meta Manager](https://metamanager.wiki/en/latest/home/installation.html#install-walkthroughs).

### Local Install Overview

Plex Image Cleanup is compatible with Python 3.10 and 3.11. Later versions may function but are untested.

These are high-level steps which assume the user has knowledge of python and pip, and the general ability to troubleshoot issues. 

1. Clone or [download and unzip](https://github.com/meisnate12/Plex-Image-Cleanup/archive/refs/heads/master.zip) the repo.

```shell
git clone https://github.com/meisnate12/Plex-Image-Cleanup
```
2. Install dependencies:

```shell
pip install -r requirements.txt
```

3. If the above command fails, run the following command:

```shell
pip install -r requirements.txt --ignore-installed
```

At this point Plex-Image-Cleanup has been installed, and you can verify installation by running:

```shell
python plex_image_cleanup.py
```

### Docker Install Overview

#### Docker Run:

```shell
docker run -v <PATH_TO_CONFIG>:/config:rw -v <PATH_TO_PLEX>:/plex:rw meisnate12/plex-image-cleanup
```
* The `-v <PATH_TO_CONFIG>:/config:rw` and `-v <PATH_TO_PLEX>:/plex:rw` flags mount the location you choose as a persistent volumes to store your files and give access to plex.
  * Change `<PATH_TO_CONFIG>` to a folder where your .env and other files are.
  * Change `<PATH_TO_PLEX>` to the folder where your Plex Folder is (It contains folders: Cache, Metadata, Plug-in Support).
  * If your directory has spaces (such as "My Documents"), place quotation marks around your directory pathing as shown here: `-v "<PATH_TO_CONFIG>:/config:rw"`

Example Docker Run command:

These docs are assuming you have a basic understanding of Docker concepts.  One place to get familiar with Docker would be the [official tutorial](https://www.docker.com/101-tutorial/).

```shell
docker run -v "X:\Media\Plex Image Cleanup\config:/config:rw" -v "X:\Plex Media Server:/plex:rw" meisnate12/plex-image-cleanup
```

#### Docker Compose:

Example Docker Compose file:
```yaml
version: "2.1"
services:
  plex-meta-manager:
    image: meisnate12/plex-image-cleanup
    container_name: plex-image-cleanup
    environment:
      - TZ=TIMEZONE #optional
    volumes:
      - /path/to/config:/config
      - /path/to/plex:/plex
    restart: unless-stopped
```

#### Dockerfile

A `Dockerfile` is included within the GitHub repository for those who require it, although this is only suggested for those with knowledge of dockerfiles. The official Plex Image Cleanup build is available on the [Dockerhub Website](https://hub.docker.com/r/meisnate12/plex-image-cleanup).

## Usage

**IMPORTANT! Due to a recent change that PLEX made (circa Jan 2023), you SHOULD restart plex before running this script. Restarting allows for all temp SQLite files to be written to the primary plex db ensuring that we know exactly which posters have been selected and should be preserved.**

**IMPORTANT: the script currently does not verify that Plex is idle before doing this. MAKE SURE that Plex is idle before running the script to avoid any database problems that may be caused by copying the DB out from under Plex while it's being optimized or the like. ONLY use this if you have a backup.**

### Notes / Tips

* Make sure that you are NOT actively updating posters or title cards with PMM or TCM while running this script. Schedule this after the last run happens. So TCM, Plex Scheduled Tasks, PMM, THEN schedule or run Plex Image Cleanup. Example: TCM @ 00:00, PLEX @ 02:00-05:00, and PMM @ 05:00
* Ensure you have proper permissions to delete/rename or the script will fail
* For performance purposes, it's recommended to run locally so that accessing the files is not done over a network share
* The script will copy the database file rather than downloading it through the Plex API. The assumption here is that you are running the script on the same machine as plex. This is useful in cases where the DB is too large to download.
* If you are using plex in docker, create a script that will perform a docker restart, sleep for about 30 seconds, and then run this script. [pbf.sh](https://github.com/bullmoose20/Plex-Stuff/blob/main/pbf.sh) is an example bash script of doing this with Plex Bloat Fix.

### Options

Each option can be applied in three ways:

1. Use the Shell Command when launching.
2. Setting the Environment Variable.
3. Adding the Environment Variables to `config/.env` 

| Option          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------:|
| Plex Path       | Path to the Plex Install Folder (Contains Folders: `Cache`, `Metadata`, `Plug-in Support`).<br>**Shell Command:** `-p` or `--plex "C:\Plex Media Server"`<br>**Environment Variable:** `PLEX_PATH=C:\Plex Media Server`                                                                                                                                                                                                                                                                                                                                                          | &#9989;  |
| Mode            | Mode to Run the Script in.<br>**Default:** `report`<br>**Options:**<br>`report`: File changes will be reported but not done.<br>`rename`: Files will be renamed in the Metadata Directory. (CAN BE RESTORED)<br>`restore`: Restores Renamed Bloat Images.<br>`clear`: Clears out the PIC Restore Directory. (CANNOT BE RESTORED)<br>`remove`: Files will be removed in the Metadata Directory. (CANNOT BE RESTORED)<br>`nothing`: Does not process any files in the Metadata Directory.<br>**Shell Command:** `-m` or `--mode remove`<br>**Environment Variable:** `MODE=remove` | &#10060; |
| Schedule        | Schedule to run in continuous mode. [Schedule Options](#schedule-options)<br>**Shell Command:** `-sc` or <code>--schedule "05:00&#124;weekly(sunday)"</code><br>**Environment Variable:** <code>SCHEDULE="05:00&#124;weekly(sunday)"</code>                                                                                                                                                                                                                                                                                                                                      | &#10060; |
| Plex URL        | Plex URL of the Server you want to connect to.<br>**If Plex URL and Plex Token are not specified it assumes a Local Run**<br>**Shell Command:** `-u` or `--url "http://192.168.1.12:32400"`<br>**Environment Variable:** `PLEX_URL=http://192.168.1.12:32400`                                                                                                                                                                                                                                                                                                                    | &#10060; |
| Plex Token      | Plex Token of the Server you want to connect to.<br>**If Plex URL and Plex Token are not specified it assumes a Local Run**<br>**Shell Command:** `-t` or `--token "123456789"`<br>**Environment Variable:** `PLEX_TOKEN=123456789`                                                                                                                                                                                                                                                                                                                                              | &#10060; |
| Discord URL     | Discord Webhook URL to send notifications to.<br>**Shell Command:** `-d` or `--discord "https://discord.com/api/webhooks/###/###"`<br>**Environment Variable:** `DISCORD=https://discord.com/api/webhooks/###/###`                                                                                                                                                                                                                                                                                                                                                               | &#10060; |
| Timeout         | Timeout can be any number greater then 0.<br>**Default:** `600`<br>**Shell Command:** `-ti` or `--timeout 1000`<br>**Environment Variable:** `TIMEOUT=1000`                                                                                                                                                                                                                                                                                                                                                                                                                      | &#10060; |
| Sleep Timer     | Sleep Timer between Empty Trash, Clean Bundles, and Optimize DB.<br>**Default:** `60`<br>**Shell Command:** `-s` or `--sleep 100`<br>**Environment Variable:** `SLEEP=100`                                                                                                                                                                                                                                                                                                                                                                                                       | &#10060; |
| Ignore Running  | Ignore Warnings the Plex is currently Running.<br>**Shell Command:** `-i` or `--ignore`<br>**Environment Variable:** `IGNORE_RUNNING=True`                                                                                                                                                                                                                                                                                                                                                                                                                                       | &#10060; |
| Local DB        | Copy Local DB instead of Downloading from the API (Helps with Large DBs).<br>**Shell Command:** `-l` or `--local`<br>**Environment Variable:** `LOCAL_DB=True`                                                                                                                                                                                                                                                                                                                                                                                                                   | &#10060; |
| Use Existing    | Use the existing database if less then 2 hours old.<br>**Shell Command:** `-e` or `--existing`<br>**Environment Variable:** `USE_EXISTING=True`                                                                                                                                                                                                                                                                                                                                                                                                                                  | &#10060; |
| Clean Transcode | Clean Plex's PhotoTranscoder Directory.<br>**Shell Command:** `-ct` or `--transcode`<br>**Environment Variable:** `CLEAN_TRANSCODE=True`                                                                                                                                                                                                                                                                                                                                                                                                                                         | &#10060; |
| Empty Trash     | Run Plex's Empty Trash Operation.<br>**Shell Command:** `-et` or `--empty-trash`<br>**Environment Variable:** `EMPTY_TRASH=True`                                                                                                                                                                                                                                                                                                                                                                                                                                                 | &#10060; |
| Clean Bundles   | Run Plex's Clean Bundles Operation.<br>**Shell Command:** `-cb` or `--clean-bundles`<br>**Environment Variable:** `CLEAN_BUNDLES=True`                                                                                                                                                                                                                                                                                                                                                                                                                                           | &#10060; |
| Optimize DB     | Run Plex's Optimize DB Operation.<br>**Shell Command:** `-od` or `--optimize-db`<br>**Environment Variable:** `OPTIMIZE_DB=True`                                                                                                                                                                                                                                                                                                                                                                                                                                                 | &#10060; |
| Trace Logs      | Run with every request and file action logged.<br>**Shell Command:** `-tr` or `--trace`<br>**Environment Variable:** `TRACE=True`                                                                                                                                                                                                                                                                                                                                                                                                                                                | &#10060; |

### Schedule Options

Schedule Blocks define how and when the script will run.

Each Schedule Blocks has 2 required parts (`time` and `frequency`) and 1 optional part (`options`) all separated with a `|`. (Example: `time|frequency` or `time|frequency|options`)

You can have multiple Schedule Blocks separated with a `,` (`time|frequency,time|frequency|options`).

#### Schedule Block Parts

* `time`: Time in the day the run will occur.
  * Time: `HH:MM` 24-hour format
  * Examples: `00:00`-`23:59` 
* `frequency`: Frequency to schedule the run. 
  * Frequencies: `daily`, `weekly(Day of Week)`, or `monthly(Day of Month)`
  * Examples: `weekly(sunday)` or `monthly(1)`
* `options`: Options changed for the run in the format `option=value`, with multiple options separated with a `;`. 
  * Options: `mode`, `transcode`, `empty-trash`, `clean-bundles`, or `optimize-db`
  * Examples: `mode=nothing` or `transcode=true`
  * **NOTE: This just overrides what you have set by the run command/environment variable**

### Schedule Block Example

```
SCHEDULE=08:00|weekly(sunday)|mode=clear,09:00|weekly(sunday)|mode=move,10:00|monthly(1)|mode=nothing;transcode=true
```

* Run at 8:00 AM on Sundays with the Options: `mode: clear`
  * `08:00|weekly(sunday)|mode=remove`
  * `time |frequency     |options`
* Run at 9:00 AM on Sundays with the Options: `mode: move`
  * `09:00|weekly(sunday)|mode=move`
  * `time |frequency     |options`
* Run at 10:00 AM on the 1st of each month with the Options: `mode: nothing` and `transcode: true` 
  * `10:00|monthly(1)|mode=nothing;transcode=true`
  * `time |frequency |options`

### Example .env File
```
PLEX_PATH=C:\Plex Media Server
MODE=report
SCHEDULE=
PLEX_URL=http://192.168.1.12:32400
PLEX_TOKEN=123456789
DISCORD=https://discord.com/api/webhooks/###################/####################################################################
TIMEOUT=600
SLEEP=60
IGNORE_RUNNING=False
LOCAL_DB=False
USE_EXISTING=False
CLEAN_TRANSCODE=False
EMPTY_TRASH=False
CLEAN_BUNDLES=False
OPTIMIZE_DB=False
TRACE=False
```