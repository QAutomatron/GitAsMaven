# GitAsMaven
Gradle script to use Git as a private Maven repository.

Currently only BitBucket is supported, as the offer free private repositories. GitHub support easily be added in a similar script.

Please find more details in [this blogpost](http://jeroenmols.com/blog/2016/02/05/wagongit/) and a full example in [this repository](https://github.com/JeroenMols/WagonGitExample).

## Prerequisites
BitBucket repository with a `releases` as its main branch, as described in [this blogpost](http://jeroenmols.com/blog/2016/02/05/wagongit/).

## Usage
1. Add the following plugin to the top of the `build.gradle` file in your library folder

  ```groovy
     apply from: 'https://github.com/QAutomatron/GitAsMaven/blob/master/publish-bitbucket.gradle'
  ```

2. Create a `gradle.properties` file within your library folder with the following parameters:

  ```groovy
  ARTIFACT_VERSION=<version_here>
  ARTIFACT_NAME=<libraryname_here>
  ARTIFACT_PACKAGE=<packagename_here>
  ARTIFACT_PACKAGING=jar
  BITBUCKET_CONSUMER=<oauth_key>
  BITBUCKET_SECRET=<oauth_secret>

  COMPANY=<bitbucket_team/company_here> //Simply your username if you're not part of a team
  REPOSITORY_NAME=<bitbucket_reponame_here>
  ```

3. Create a `gradle.properties` file in the root of your project (or better in the global `.gradle` folder on your system) with the following parameters

  ```groovy
  USERNAME=<username>
  PASSWORD=<password or application key>
  ```

  Note: Do not check this file into version control!

4. Run the following command to upload a version to your Maven repository.

  ```bash
  ./gradlew uploadArchives
  ```
