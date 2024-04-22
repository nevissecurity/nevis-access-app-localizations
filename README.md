![Nevis Logo](https://www.nevis.net/hubfs/Nevis/images/logotype.svg)

# Nevis Access App Localizations

This repository contains the base `localizations.csv` file for the [Nevis Access App](https://docs.nevis.net/nevisaccessapp/) which contains all translation keys and default values for all supported languages.
Nevis supplies standard translations of all app messages.


The `localizations.csv` is used in our [Ordering an Access app](https://docs.nevis.net/nevisaccessapp/ordering-an-access-app) process when a customer orders a branded Access application. For more information about the purpose of `localizations.csv` file and its structure read the corresponding [chapter](https://docs.nevis.net/nevisaccessapp/ordering-an-access-app#localizations).

The purpose of publication of `localizations.csv` file is to ease to follow its changes for the customers. At every new release of the Nevis Access application a new `localizations.csv` will be published and tagged, this way newly introduced translation keys and modified values for existing transation keys can be easily checked in history.  
The [release tags](https://github.com/nevissecurity/nevis-access-app-localizations/tags) indicate a specific, released Access App version - for example `releases/2.6.x`. The `next` tag indicates the `localizations.csv` file for the next unreleased Access App version.

# Custom translations

In case no specific, custom values are defined (per translation key), the default translations will be used.
When providing custom translations, only *changed* translation key-value entries must be supplied.

Provide the changed `localizations.csv` file via the [Nevis Portal Ticketing System](https://portal.nevis.net/).
Keep the formatting of the file in place. Every entry must be comma separated and enclosed with `"`.
We cannot accept spreadsheet files like Microsoft Excel.

# Comparing localization versions

There are several ways you're able to compare different localization versions.

## GitHub Compare feature

Use the [GitHub compare feature](https://github.com/nevissecurity/nevis-access-app-localizations/compare) to get a complete set of all changes, simply select the two tags you're interested in.

## Find missing keys bash script

If you want to easily find out whether new translation keys have been added, the following bash script can help you.
It takes two .csv files as input arguments and will list all missing keys in the second .csv file.

```
#!/bin/bash

# Check if two file names are passed as arguments
if [ $# -ne 2 ]; then
  echo "Error: Please provide the names of two files as arguments."
  exit 1
fi

# Store the first column of each file in separate arrays
file1=($(cut -d ',' -f 1 "$1"))
file2=($(cut -d ',' -f 1 "$2"))

# Iterate over each element in the first array
echo "The following keys are missing in the second .csv file:"
echo ""
for i in "${file1[@]}"; do
  # Check if the current element is not in the second array
  if ! [[ " ${file2[@]} " =~ " ${i} " ]]; then
    # If not, print the missing element
    echo $i
  fi
done
```

1. Add the lines to a file, for example compare.sh
2. Make the script executable: chmod +x compare.sh
3. Usage: `./compare.sh next/localizations.csv 2.7.x/localizations.csv`

# Communication

- Check our [app documentation](https://docs.nevis.net/nevisaccessapp/)
- Visit our [website](https://www.nevis.net/en/solution/authentication-cloud)
- Contact us on email: [sales@nevis.net](mailto:sales@nevis.net)

© 2024 made with ❤ by Nevis
