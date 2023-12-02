# 👩💻 Contributing

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption><p>High-Level Architecture of the Main Framework Used in the Application</p></figcaption></figure>

## Setup from the ground up 🌱

### 1. Installation of Nvm

* [NVM for Windows](https://github.com/coreybutler/nvm-windows)
* [NVM for Ubuntu](https://github.com/nvm-sh/nvm#installing-and-updating)

### 2. Installation of npm/node.js

```
nvm install lts
nvm use lts
```

{% hint style="info" %}
If this step doesn't work, try ...
{% endhint %}

### 3. Clone the repository

{% tabs %}
{% tab title="HTTPS" %}
```
git clone https://github.com/MEDomics-UdeS/MEDomicsLab.git
```
{% endtab %}

{% tab title="SSH" %}
```
git clone git@github.com:MEDomics-UdeS/MEDomicsLab.git
```
{% endtab %}
{% endtabs %}

### 4. Setup server side (Go)

#### 4.1 Installation of Go

1. Download the latest stable release of Go from the official website: [https://golang.org/dl/](https://golang.org/dl/)
2. Follow the [installation instructions](https://go.dev/doc/install) for your operating system.

#### 4.2 Setup of environment

{% tabs %}
{% tab title="Windows" %}
Execute these commands in a **cmd** prompt:

```
setx GOPATH %USERPROFILE%\go
setx PATH "%PATH%;C:\Go\bin"
```
{% endtab %}

{% tab title="Linux and Mac" %}


Execute these commands in a terminal:

```
echo 'export PATH=$PATH:/usr/local/go/bin' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOPATH/bin' >> $HOME/.bashrc
```
{% endtab %}
{% endtabs %}

After, **close all your terminals** because these commands will take effects on the initialisation of any terminal

#### 4.3 Verify installation

1. Open a new terminal
2. Run the command `go version`
3. If Go is installed correctly, you should see the version number printed to the console.

#### 4.4 Setup for the application

1. Open a new command prompt and go to the `<repo path>/go_server` directory.
2. Run the command `go run main.go` (on first time, it should download requiered libraries and lunch the server)
3. you can terminate the process by pressing `CTRL + C`
4. Then build the app by running `go build main.go` (It should create an executable file -> that file will be run by the client side javascript so modification to .go files must be followed by a rebuild) Congratulations, you're now ready to start developing Go applications!

### 5. Init submodules

```
cd <.../MEDomicsLab/>
git submodule init
git submodule update --init --recursive --remote
cd pythonCode/submodules/MEDimage
git checkout dev_lab
cd ../MEDprofiles
git checkout fusion_MEDomicsLab
```

### 6. Start the electron app !

{% code fullWidth="false" %}
```
cd <.../MEDomicsLab>
npm install
nprm run dev
```
{% endcode %}

{% hint style="info" %}
#### Modify startup settings

1. Go to file `medomics.dev.js`
2. Here is a description of the Object:

```javascript
const config = {
  // If true, the server will be run automatically when the app is launched
  runServerAutomatically: true,
  // If true, use the react dev tools
  useRactDevTools: false,
  // the default port to use for the server, be sure that no programs use it by default
  defaultPort: 5000,
  // Either "FIX" or "AVAILABLE" (case sensitive)
  // FIX 		-­> if defaultPort is used, force terminate and use defaultPort
  // AVAILABLE 	-> if defaultPort is used, iterate to find next available port
  portFindingMethod: PORT_FINDING_METHOD.FIX
}
```
{% endhint %}

## To Test the Production Build&#x20;

### Build the Electron app and Run the built version

{% tabs %}
{% tab title="Windows" %}
```
npm run build:win                            # build and package the application 
.\build\dist\win-unpacked\MEDomicsLab.exe    # Run the executable of the built version
```
{% endtab %}

{% tab title="Linux" %}
```
npm run build:linux                    # build and package the application 
bash build/dist/linux-unpacked/medapp  # Run the executable of the built version
```
{% endtab %}

{% tab title="Mac" %}
```
npm run build:mac                                                    # build and package the application 
bash build/dist/mac-arm64/MEDomicsLab.app/Contents/MacOS/MEDomicsLab # Run the executable of the built version     
```
{% endtab %}
{% endtabs %}

> The built app will be located in the `build/dist` folder
