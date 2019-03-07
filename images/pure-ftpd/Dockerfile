FROM stilliard/pure-ftpd

CMD /run.sh -c $MAX_CLIENTS -C $MAX_REQUESTS_PER_IP -l puredb:/etc/pure-ftpd/pureftpd.pdb -E -R -P $PUBLICHOST -d -O w3c:/var/log/pureftpd.log