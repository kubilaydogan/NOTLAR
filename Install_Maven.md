## Step-by-Step Guide to Install and Configure Maven on macOS

### 1. Install Maven
- **Using Homebrew**:
  ```sh
  brew install maven
  ```

### 2. Verify Installation

```sh
mvn -version
```

### 3. Configure Maven
- **Set Environment Variables**:
    - Open the `.zshrc` file:
      ```sh
      nano ~/.zshrc
      ```
    - Add the following lines to set the `M2_HOME` and `MAVEN_HOME` environment variables:
      ```sh
      export M2_HOME=/usr/local/Cellar/maven/<version>/libexec
      export MAVEN_HOME=/usr/local/Cellar/maven/<version>/libexec
      export PATH=$PATH:$M2_HOME/bin
      ```
    - Replace `<version>` with the installed Maven version.
    - Save and close the file.


- **Apply the Changes**:
  ```sh
  source ~/.zshrc
  ```

