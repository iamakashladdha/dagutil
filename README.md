# Overview
This repository is meant to contain scripts to assist customers to Pause/Unpause Dags in Software and Astro as needed. See usage instructions below

# Pre-requisites
- Python 3

# Setup
  1. Use the command 'https://github.com/iamakashladdha/dagutil.git' to clone this repo
  2. Use the command `cd dagutil` to change your working directory
  3. Run the `python3 init-connections.py` command to generate the `airflow-connections.yaml` file
  4. In the `airflow-connections.yaml` update variables to match your target i.e. Software deployment and Astro deployments
 
  - Astro
    - Astro Domain: From the Astronomer UI in the Astro product, this is the URL of your deployment after clicking the `Open Airflow` button (be sure to remove `/home` from the end of the URL
    - Astro Key ID: From the Astronomer UI in the Astro product, this is found in the **API Keys** section of your deployment
    - Astro Key Secret: From the Astronomer UI in the Astro product, this is found in the **API Keys** section of your deployment
  
  - Software
    - Software API Key: From the Astronomer UI in the Software product, this is found under the **Service Accounts** section
    - Software Base Domain: From the Astronomer UI in the Software product, this is retrievable from the URL shown in your browser. Your URL will have the following format: `https://app.<BASE-DOMAIN>/w/<WORKSPACE-ID>/d/<DEPLOYMENT-RELEASE-NAME>`, you'll only need the <BASE-DOMAIN> piece.
  - Software Deployment Release Name: From the Astronomer UI in the Software product, this is retrievable from the URL shown in your browser. Your URL will have the following format: `https://app.<BASE-DOMAIN>/w/<WORKSPACE-ID>/d/<DEPLOYMENT-RELEASE-NAME>`,  you'll only need the <RELEASE-NAME> piece.

# Execution Commands
*After completing the setup section above, you may use the following make commands:*
- Use the `python3 dagstate.py <target> <action> <daglist>` command to execute the utility to pause/unpause Dag's
    - target: Accepted Values are `Software` or `Astro`
    - action: `Pause` or `Unpause` Dags
    - daglist: Text file name, having list of dags with one line for each dag in input folder. Example daglist.txt
    - sample command: python3 dagstate.py astro unpause daglist.txt 
    - sample command: python3 dagstate.py software pause daglist.txt
