# Language XML Stream v1.0

These scripts are used to extract the language pack xml files from the Joomla! download site and make them statically publicly available.

# Okay, Lets get started... ˘Ô≈ôﺣ

Should you like to contribute any improvements either in code or conduct, just open an issue as the first step, and beginning of the conversation. ツ

## Setup the Builder

Clone this repository
```bash
$ git clone https://github.com/llewellynvdm/Joomla-XML-Lang-stream.git
$ cd Joomla-XML-Lang-stream/
```

## Run the Builder

Make sure that the following files are executable.
```bash
$ sudo chmod +x run.sh
```

Start the Building process
```bash
$ ./run.sh
```

# Help Menu
```txt
Usage: ./run.sh [OPTION...]

You are able to change a few default behaviours in the XML Static File extractor
  ------ Passing no command options will fallback on the defaults -------

	Options ᒡ◯ᵔ◯ᒢ
	======================================================
   --endpoint=<url>
    set the endpoint of the xml retrieval

    example: ./run.sh --endpoint=https://downloads.joomla.org/index.php?option=com_languagepack&view=export&format=xml
    ======================================================
   --version-key=<word>
    set the version key used in URL

    example: ./run.sh --version-key=cms_version
    ======================================================
   --language-key=<word>
    set the language key used in URL

    example: ./run.sh --language-key=language_code
    ======================================================
   --mapper=<path>
    set all the mapper details with a file
    the repo/conf/mapper.tmp has more details of the format

    example: ./run.sh --conf=/home/username/.config/xml-stream-mapper.conf

    defaults:
        - repo/conf/.mapper
    ======================================================
   --push
	push changes to github (only if there are changes)
		- must be able to push (ssh authentication needed)

	example: ./run.sh --push
    ======================================================
   --target-folder=<path>
    set folder where we place the XML static files

    example: ./run.sh --conf=/home/username/public_html/xml/

    defaults:
        - repo/src/
    ======================================================
   --conf=<path>
    set all the config properties with a file

    example: ./run.sh --conf=/home/username/.config/xml-stream.conf

    defaults:
        - repo/conf/.config
    ======================================================
   --dry
    To show all defaults, and not update repo

    example: ./run.sh --dry
    ======================================================
   -q|--quiet
    Quiet mode that prevent whiptail from showing progress

    example: ./run.sh -q
    example: ./run.sh --quiet
    ======================================================
   -h|--help
    display this help menu

    example: ./run.sh -h
    example: ./run.sh --help
    ======================================================
            Joomla XML Stream v1.0
    ======================================================
```

# Setup Cron Job

To run this in a crontab
```bash
$ crontab -e
```
Then add the following line, update the time as needed
```bash
10 5 * * MON /home/username/Joomla-XML-Lang-stream/run.sh -q >> /home/username/Joomla-XML-Lang-stream/stream.log 2>&1
```

# Use GitHub Actions

You will need to setup a list of secrets in your fork of the XML_STREAM.

> The github user email being used to build
- XML_STREAM_GIT_EMAIL
> The github username being used to build
- XML_STREAM_GIT_USER
> `gpg -a --export-secret-keys >myprivatekeys.asc`
> The whole key file text from the above myprivatekeys.asc
> This key must be linked to the github user being used
> This is used to sign the push changes if there are any
- XML_STREAM_GPG_KEY
> The name of the myprivatekeys.asc user
- XML_STREAM_GPG_USER
> A id_ed25519 ssh private key liked to the github user account
- XML_STREAM_SSH_KEY
> A id_ed25519.pub ssh public key liked to the github user account
- XML_STREAM_SSH_PUB

All these secret values are needed to fully automate the build. Then you need to go to the actions are in your fork of XML_STREAM and activate the actions.

### Free Software
```txt
Copyright (C) 2019. All Rights Reserved
GNU/GPL Version 2 or later - http://www.gnu.org/licenses/gpl-2.0.html
```

