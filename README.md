After installing kubectl 
UNZIP istio-1.17.1.zip
INSTALLING ISTIO IN OUR CLUSTOR

--------------------------------------------------------------------------------------------------------------------------------
1. Go to the Istio release page to download the installation file for your OS, or download and extract the latest release automatically (Linux or macOS) or you can use the zip i have provided:

    $ curl -L https://istio.io/downloadIstio | sh -

2. Move to the Istio package directory. For example, if the package is istio-1.17.1:
    
    cd istio-1.17.1

3. Add the istioctl client to your path (Linux or macOS): 

    $ export PATH=$PWD/bin:$PATH

4. For this installation, we use the demo configuration profile. It’s selected to have a good set of defaults for testing,
   but there are other profiles for production or performance testing.

    $ istioctl install --set profile=demo -y


Type istioctl to check if the istio is running

5. Add a namespace label to instruct Istio to automatically inject Envoy sidecar proxies when you deploy
   your application later:

    $ kubectl label namespace development istio-injection=enabled

--------------------------------------------------------------------------------------------------------------------------------

After istio installation, setup the kuantam gateway with jwt authentication and authorization policies.


KUANTAM GATEWAY INSTALLATION
--------------------------------------------------------------------------------------------------------------------------------

Installing gateway in development namespace

1. Create a new namespace called development

    $ kubectl create namespace development

2. Enable gateway in development namespace

    $ kubectl apply -f kuantam-gateway.yaml

3. Enable authentication policy

    $ kubectl apply -f kuantam-authentication.yaml

4. Enable authorization policy

    $ kubectl apply -f kuantam-authorization.yaml

Now our gateway is ready

--------------------------------------------------------------------------------------------------------------------------------