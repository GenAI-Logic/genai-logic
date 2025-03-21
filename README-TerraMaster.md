# Welcome to GenAI-Logic

Thankyou for installing!  We very much appreciate your interest, and are determined to make your experience as productive as possible.

Issues?  Email us at `support@genai-logic.com`

&nbsp;

## Prerequisites for installing API-in-a-Box™

It is recommended to get a local copy of WebGenAI:
1. Choose an install location (e.g., `~/dev/genai-logic`)
    * This should have sufficient disk space for your systems, including the databases
2. Download and unzip this project, either [from here](https://github.com/GenAI-Logic/genai_logic) (see screenshot at end), or using curl:
```bash
cd genai-logic
curl -LJO https://github.com/GenAI-Logic/genai-logic/archive/refs/heads/main.zip
unzip genai-logic-main.zip
cd genai-logic-main
```
3. We'll use a local editor to open the you IDE to this location
4. Update your `webgenai/docker-compose-webg.yml`:
    1. Copy the license key you received in the registration email over: `- GENAI_LOGIC_APIKEY=<paste license here from registration email>`
        * If you have not already registered, please visit the [registration page](http://registration-genailogic.com/registration.html) to obtain a license key.
    5. GenAI-Logic uses OpenAI, which requires an Open API Key:
        1. Obtain a Key
            1. Obtain one from [here](https://platform.openai.com/account/api-keys) or [here](https://platform.openai.com/api-keys)
            2. Authorize payments [here](https://platform.openai.com/settings/organization/billing/overview)
        2. Update the key in this line: `- APILOGICSERVER_CHATGPT_APIKEY=<sk-proj-your-openai-key-here>`.

![install-setup](webgenai/images/terra-master-desktop-with-docker-manager.png)

&nbsp;

## To Run WebGenAI

Once you have installed (above), start the server:

```bash
sh run_web_genai.sh
```

Open your browser at [http://localhost:8282](http://localhost:8282).

Find the [documentation here](https://apilogicserver.github.io/Docs/WebGenAI/).

&nbsp;

## Verify the installation

Open your browser at [http://localhost:8282/admin-app/#/Home?demo=genai_demo](http://localhost:8282/admin-app/#/Home?demo=genai_demo), and follow these steps:

![install-setup](./webgenai/images/1-create-demo.png)
![install-setup](./webgenai/images/2-open-app.png)
![install-setup](./webgenai/images/3-landing-page.png)
![install-setup](./webgenai/images/4-customer.png)
![install-setup](./webgenai/images/5-item-upd.png)

The constraint is produced by the business logic:
* The quantity change recomputed the amount (rule 4)
* The amount adjusted the amount_total (rule 3)
* The amount_total adjusted the balance (rule 2)
* The balance exceeded the credit limit (rule 1), which produced the message and reverted the transaction

```bash
Use case: Check Credit    
    1. The Customer's balance is less than the credit limit
    2. The Customer's balance is the sum of the Order amount_total where date_shipped is null
    3. The Order's amount_total is the sum of the Item amount
    4. The Item amount is the quantity * unit_price
    5. The Item unit_price is copied from the Product unit_price
```

&nbsp;

## Run WebGenAI samples

After installation, you can try the sample prompts at `samples/web-genai-samples`.

&nbsp;

## Run API Logic Server samples 

Installation not required.

Your install includes a few sample systems at: samples.

To run the default sample:

```bash
sh run_sample.sh nw_sample
```

And then open your browser at [http://localhost:5656](http://localhost:5656).

To run a different sample, replace `nw_sample` with the sample directory.  Only 1 sample can be running at a time.

| Sample | Notes   |
| :------------- | :------------- |
| nw_sample | Our take on Northwind (Customers, Orders etc), **with logic.**<br>&nbsp;&nbsp;&nbsp;&nbsp;1. Illustrates key functionality<br>&nbsp;&nbsp;&nbsp;&nbsp;2. Extensive [Tutorial](https://apilogicserver.github.io/Docs/Tutorial/) and code/logic examples |
| nw_sample_nocust | Uncustomized version of nw, created in about 5-10 seconds.<br>&nbsp;&nbsp;&nbsp;&nbsp;* Illustrates results you should obtain using your existing databases |

&nbsp;

## Creating projects from existing databases

Coming soon

&nbsp;

## Debugging Projects in VSCode

Coming soon

## Acquire from git

![acquire](webgenai/webg_config/acquire.png)
