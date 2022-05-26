FROM debian

RUN apt-get update \
  && apt-get install -qq -y --no-install-recommends \
  netcat \
  && apt-get autoremove -y \
  && rm -rf /var/lib/apt/lists/*

# stamp build time within image.
RUN date --utc +'%s' | tee date.tmp

# If it has been less than ten minutes since build, exit.
# If now is more than ten minutes since build, listen TCP port 80.
CMD date && date -d @1653550886 && if [ $((`date +'%s'` - 1653550886 )) -lt 0 ]; then exit 100; else echo 'START'; sleep infinity; fi
