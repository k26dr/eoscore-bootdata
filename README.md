# EOS CORE Bootdata

1. Copy `genesis.json` and `config.ini` into a new directory and `cd` into it
2. Modify `config.ini` as specified in the file
3. Run nodeos:

If resyncing from a previous bad chain or syncing a fresh chain

`nodeos --config-dir . --data-dir . --delete-all-blocks --genesis-json genesis.json`

If starting from an existing chain:

`nodeos --config-dir . --data-dir .`

## Adding Peers

If you want your peer added to our peer list, send a pull request with your peer added to `config.ini`. 

You can add peers manually at the bottom of your `config.ini`


## Connecting with Wireguard 

Use the following to connect to the network via the Wireguard VPN mesh:

```
./stop.sh
rm -r state
rm -r blocks
nano config.ini
# Add the following
p2p-peer-address = 40.85.223.230:9874
p2p-peer-address = 40.85.223.230:9875
p2p-peer-address = 40.85.223.230:9873
# COMMENT OUT ALL OTHER PEERS
# Change your p2p port (if you had 9876, change it to 9875 or something) which goes on on your p2p-listen-endpoint and p2p-server-address
# Save and exit
./start.sh --delete-all-blocks --genesis-json ~/kbfs/team/eos_ghostbusters/jun4/genesis.json
tail -F stderr.txt
# First couple thousand blocks are heavy so it may take a while

# Once you are fully synced to head block num 11778, you are on the correct chain. At this point, you can revert back to your old p2p port, delete p2p-peer-address = 40.85.223.230:9874, p2p-peer-address = 40.85.223.230:9875, p2p-peer-address = 40.85.223.230:9873 from your config.ini, re-connect with your Ghostbusters peers using the scripts, and restart
./start.sh
```
