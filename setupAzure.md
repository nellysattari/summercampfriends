## Create resource group
az group create  --location australiaeast --name summer-camp-friends

## create storage account
az storage account create --name summercampfriendsblob --resource-group summer-camp-friends --location australiaeast --sku Standard_ZRS --encryption blob

## Get account storage key
### az storage account keys list -g MyResourceGroup -n MyStorageAccount
az storage account keys list -g summer-camp-friends -n  summercampfriendsblob
## Create a container for blobs (DIDNOT WORK)
IT NEEDS AUTH mode
az storage blob list my-container
export AZURE_STORAGE_ACCOUNT=summercampfriendsblob
export AZURE_STORAGE_ACCESS_KEY=QLCz5aq+11ZsG1pWTk50XXs38TZka0A5I8pFvPywsYDRLVhqgdEWSSREYDyAjrrGKyhnkrxoo3lNDYVO3HBFcQ==
 
az storage container create   --account-name summercampfriendsblob  --name summercampfriendscontainer   
az storage container create -n summercampfriendscontainer  --account-key AZURE_STORAGE_KEY


az storage blob upload dist/*.*  summercampfriendscontainer 

az storage blob copy start-batch --account-key QLCz5aq+11ZsG1pWTk50XXs38TZka0A5I8pFvPywsYDRLVhqgdEWSSREYDyAjrrGKyhnkrxoo3lNDYVO3HBFcQ== --account-name summercampfriendsblob --destination-container summercampfriendscontainer  