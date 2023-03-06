# Nolus snapshot
# Chain-id: nolus-rila
# Size: 5GB


Stop node, delete data
```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```
Download data from snapshot
```
mkdir $HOME/.nolus/data
wget -O - http://65.108.78.116/nolus/nolus-rila_latest.tar | tar xf - -C $HOME/.nolus/data
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```
Start node
```
sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```
Done!
