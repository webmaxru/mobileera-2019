## Export/import data

Retrieving Google Cloud Account Credentials
- Visit the Firebase Console
- Select your project
- Navigate to Project Settings (at the time of writing the gear icon button at the top left of the page).
- Navigate to Service Accounts
- Click Generate New Private Key
- This downloaded json file contains the proper credentials needed for node-firestore-import-export to authenticate. Rename to `./serviceAccount.json`
- Create `./backups` folder
- You can safely store `backups` folder and `serviceAccount.json` file locally - they are in .gitignore

https://www.npmjs.com/package/node-firestore-import-export
```console
npm install node-firestore-import-export
```

## Export data
__IMPORTANT!__ Always do a fresh export before editing/importing data, someone else could do some changes, so you might destroy these.
```console
npx firestore-export --accountCredentials ./serviceAccount.json --backupFile ./backups/firestore.json
```

## Import data
__IMPORTANT!__ All existing data with IDs will be overwritten. Non-existing in import file IDs will NOT be removed from database.
```console
npx firestore-import --accountCredentials ./serviceAccount.json --backupFile ./backups/firestore.json
```
