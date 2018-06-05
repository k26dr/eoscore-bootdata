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
