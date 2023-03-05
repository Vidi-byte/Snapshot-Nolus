# Snapshot-Nolus
v0.1.43

#### Stop the service and reset the data
```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```

#### Download latest snapshot
```
curl -L http://194.163.187.175/nolus/nolus.tar.lz4 | tar -Ilz4 -xf - -C $HOME/.nolus
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```

#### Restart the service and check the log
```
sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```
