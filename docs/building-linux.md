## Build instructions for Linux using Docker

### Obtain your API credentials

You will require **api_id** and **api_hash** to access the Telegram API servers. To learn how to obtain them [click here][api_credentials].

### Clone source code

    git clone --recursive https://github.com/frankwalter1301/tkiller.git

### Prepare libraries

Go to the `tdesktop` directory and run

    docker build -t tdesktop:centos_env Telegram/build/docker/centos_env/

### Building the project

Make sure that you're still in the `tdesktop` directory and run (using official android telegram or [your](#obtain-your-api-credentials) **api_id** and **api_hash**)

    docker run --rm -it \
        -v $PWD:/usr/src/tdesktop \
        tdesktop:centos_env \
        /usr/src/tdesktop/Telegram/build/docker/centos_env/build.sh \
        -D TDESKTOP_API_ID=4 \
        -D TDESKTOP_API_HASH=014b35b6184100b085b0d0572f9b5103 \
        -D DESKTOP_APP_USE_PACKAGED=OFF \
        -D DESKTOP_APP_DISABLE_CRASH_REPORTS=OFF

Or, to create a debug build, run (also using official android telegram or [your](#obtain-your-api-credentials) **api_id** and **api_hash**)

    docker run --rm -it \
        -v $PWD:/usr/src/tdesktop \
        -e DEBUG=1 \
        tdesktop:centos_env \
        /usr/src/tdesktop/Telegram/build/docker/centos_env/build.sh \
        -D TDESKTOP_API_ID=4 \
        -D TDESKTOP_API_HASH=014b35b6184100b085b0d0572f9b5103 \
        -D DESKTOP_APP_USE_PACKAGED=OFF \
        -D DESKTOP_APP_DISABLE_CRASH_REPORTS=OFF

The built files will be in the `out` directory.

[api_credentials]: api_credentials.md
