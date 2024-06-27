# Avalanche Create a Custom Subnet

The HyperSDK provides the ability to create a custom virtual machine, which offers complete control over a custom blockchain. With the HyperSDK, you can design a blockchain that perfectly suits your needs, such as creating and transferring tokens or implementing a traditional order book for asset trading. This level of customization provides a powerful tool for businesses and organizations seeking a tailored solution.


## Description 
```consts/consts.go``` contains the constants that is accessible across the hyperVM. The HRP, Name, and Symbol constants define information about the TokenVM, including its Human-Readable Part (HRP), name, and symbol.
```GO
const (
	// TODO: choose a human-readable part for your hyperchain
	HRP = "Srishti"
	// TODO: choose a name for your hyperchain
	Name = "Sri"
	// TODO: choose a token symbol
	Symbol = "SK"
)
```
This code is added in the ```consts/consts.go```.

```registry/registry.go``` contains the action that will be performed in the terminal during interaction.
```GO
// TODO: register action: actions.CreateAsset
consts.ActionRegistry.Register(&actions.CreateAsset{}, actions.UnmarshalCreateAsset, false),
// TODO: register action: actions.MintAsset
consts.ActionRegistry.Register(&actions.MintAsset{}, actions.UnmarshalMintAsset, false),
```
This code is added in ```registry/registry.go```

## Steps of Execution
This project is execute on WSl on windows and GO installed inside wsl.<br>
1) run ```git clone https://github.com/Sriisshti/Advance-mod-2/tree/root```
2) run this github clone in vs code
3) As some files show last year because in the clone those were added by metacrafters year ago .
4) In terminal run command ```MODE="run-single" ./scripts/run.sh``` and this will start our machine with 1 subnet and for 2 subnet run ```./scripts/run.sh```. 
5) To start interaction run ```./scripts/build.sh```. output will be :
This command will put the compiled CLI in ./build/token-cli.
6) Lastly, we'll need to add the chains we created and the default key to the token-cli. run command:
```javascript
./build/token-cli key import demo.pk
./build/token-cli chain import-anr
```
chain import-anr connects to the Avalanche Network Runner server running in the background and pulls the URIs of all nodes tracking each chain you created..

## Creation and Minting process
### Step 1 Asset Creation
To create an assest run the command:
```javascript
./build/token-cli action create-asset
```
Enter the metadata and confirm
<b>NOTE - txID is the assetID of your new asset.</b>

### Step 2 Minting of asset
To mint the created assest run command:
```javascript
./build/token-cli action mint-asset
```
enter the assetID then enter the receipient then enter the amount and continue.

### Step3 check balance
run the command:
```javascript
./build/token-cli key balance
```
and enter the assetID of the token .

### Transfer assets
spilt terminal and in 1st run the command 
```javascript
./build/token-cli chain watch
```
enter 0 and execute it
in second terminal run
```javascript
./build/token-cli action transfer
```
then enter the assetID which we earlier created and enter the recepient address in this case we are don't have other address so we will transfer to ourself and see the transaction in first terminal. enter the amount and continue.

### Closing 
run the command 
```javascript
killall avalanche-network-runner
```
This will close the blockchain we have just deployed.