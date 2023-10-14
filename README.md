# React Native Gradle Automation and Play Store Deployment Action

**Overview:**

This action is designed to simplify the development and distribution process of your React Native applications. Whether you're looking to automate the Gradle file update before each build or streamline the release process to the Play Store, this action provides the ideal solution.

Additionally, the number of builds in the build.gradle file is automatically updated with the workflow execution count.

## Usage

**Requirements:**

- A React Native application.
- A Google Play Console service account with access to your applications.
- A Google Play Console service account JSON key file (SERVICE_ACCOUNT_JSON) in your repository. If SERVICE_ACCOUNT_JSON is not set, this action will still handle artifact uploads.

**Getting Started:**

1. Ensure that you meet the prerequisites mentioned above.
2. Add this action to your GitHub Actions workflow.
3. Configure the necessary environment variables in your repository, including *VARSLIST* if available.
4. The action will automatically manage Gradle file updates before each build and automate Play Store releases as required.

**VARLIST**
1. **Required**
   - KEYSTORE64
   - ANDROID_KEY_PASSWORD
   - ANDROID_ALIAS
   - ANDROID_ALIAS_PASS
2. **Optional**
   - NPM_TOKEN
   - SERVICE_ACCOUNT_JSON


### Usage
```yml
jobs:
  build-android-app:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - uses: AndreaMolinari/RNAndroidBuild@v1.0.0
        with:
          package-name: com.android.example
          KEYSTORE64: ${{ secrets.KEYSTORE64 }}
          ANDROID_KEY_PASSWORD: ${{ secrets.ANDROID_KEY_PASSWORD }}
          ANDROID_ALIAS: ${{ secrets.ANDROID_ALIAS }}
          ANDROID_ALIAS_PASS: ${{ secrets.ANDROID_ALIAS_PASS }}
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
          SERVICE_ACCOUNT_JSON: ${{ secrets.SERVICE_ACCOUNT_JSON }}
```

## License
This project is licensed under the MIT License - See the [LICENSE](LICENSE) file for more details.