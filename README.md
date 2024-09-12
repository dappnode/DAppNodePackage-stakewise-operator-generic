# StakeWise Operator DAppNode Package

This package allows you to run a **StakeWise Operator** node on your DAppNode device. The **StakeWise Network** enables anyone capable of running Ethereum validators to participate in liquid staking and receive staking delegations from others by creating a vault in the [Stakewise App](https://app.stakewise.io/operate)

### Services

This package includes the following services:

- **StakeWise Operator (`operator`)**:

  - The operator node is responsible for managing your vault and validator operations within the StakeWise ecosystem. It interacts with both the execution and consensus layers of Ethereum.

  - Configuration files for the operator are stored in `/data/operator/config`. The logs are located in `/data/operator/logs`.

  - The operator node handles the creation of the `deposit_data.json` file and the corresponding validator keys, which will be uploaded to the Web3Signer running on your Dappnode

- **Staker Tools Integration**:

  - This package includes `dvt_lsd_tools.sh` sourced from the `staker-package-scripts` repository. It is downloaded during the Docker build process and placed in `/etc/profile.d/`. This script helps manage staking-related processes within the StakeWise operator node.

### Configuration

The setup wizard allows you to configure the StakeWise Operator during installation. You can set the following fields:

1. **Vault Contract Address**: Enter the contract address of your StakeWise vault. This is required to link your operator to the correct vault on the StakeWise network.
2. **Number of Validators**: Define how many validators your operator will manage.

You can also leave these fields blank and restore them later by uploading a backup that includes your configuration.

### Backup and Restore

- **Backup**: The package provides a backup feature to save important configuration and data files, such as the operator's vault contract address and mnemonic. This is crucial for securing your operator's state.

- **Restore**: You can restore a previously saved backup by uploading the relevant files, such as `mnemonic.txt` or the vault configuration.

It's highly recommended that you download and store your backup securely after the operator setup.

### Monitoring

- **Prometheus Metrics**:

  The operator exposes Prometheus metrics for monitoring the node’s performance and health, which are accessible on port `8008`.

### Steps to Become a StakeWise Operator

1. **Create Your Vault**: First, create your vault on the [StakeWise platform](https://app.stakewise.io/operate). Follow the steps to configure your vault and note down the vault contract address.

2. **Install the StakeWise Operator Package**: Install the package on your DAppNode and complete the setup by entering the **Vault Contract Address** and specifying the number of validators.

3. **Backup Your Configuration**: After the initial configuration, download a backup of your operator’s configuration to store it securely.

4. **Upload Deposit Data**: After generating validator keys, upload the `deposit_data.json` file to your vault on the [StakeWise platform](https://app.stakewise.io/operate).

5. **Manage Your Mnemonic**: The mnemonic used for validator key generation should be secured. You can download it from the backup and store it safely.

6. **Validator Management**: You can increase the number of validators through the package configuration. The operator will create additional keys and upload the deposit data as needed.

---

For more detailed instructions and information, visit the [StakeWise documentation](https://stakewise.io/#home).
