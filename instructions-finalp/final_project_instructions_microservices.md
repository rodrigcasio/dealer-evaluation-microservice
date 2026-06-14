::page{title="Final Project(Option B: JavaScript): Product Price Comparison Application"}

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-CD0101EN-SkillsNetwork/images/IDSN-logo.png" width="200" alt="cognitiveclass.ai logo">

## 
**Estimated Time Needed:** 1.5 hours

-  In this final project, you will be deploying multiple microservices to create an integrated application. These components consist of two backend microservices developed in JavaScript and Node.js, complemented by a front-end microservice.

## Learning objectives:

After completing this lab, you will be able to:

- Create an application consisting of multiple microservices
- Deploy the back-end microservice on IBM Cloud Code Engine
- Deploy the front-end microservice on IBM Cloud Code Engine

::page{title="Final Project"}

###  Note:

1. Please ensure that all updates to the files are properly saved.

2. Capture the screenshots as mentioned in the respective tasks.

3. You can submit your project deliverables through either Option 1: AI-Graded Submission and Evaluation or Option 2: Peer-Graded Submission and Evaluation.

4. **For Option 1: AI-Graded Submission and Evaluation** and  **Option 2: Peer-Graded Submission and Evaluation**  - Submission requires the screenshots for all the **Tasks 1-9.**

::page{title="Part A: Deploy the Backend Microservices"}

1. Open the Code Engine CLI.

2. Deploy the microservice for Product Details, which provides API endpoints to retrieve product information.

**build-source** - `https://github.com/ibm-developer-skills-network/wzpvw-dealer_evaluation_backend_js.git`

**build-context-dir** - `products_list`

**port** - `5000`

```
ibmcloud ce application create --name prodlist --image us.icr.io/${SN_ICR_NAMESPACE}/prodlist --registry-secret icr-secret --port 5000 --build-context-dir products_list --build-source https://github.com/ibm-developer-skills-network/wzpvw-dealer_evaluation_backend_js.git
```
> Copy the deployment URL and save it in a notepad or other text editors.

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the successful deployment and save it as `product_details_deploy.png` or `product_details_deploy.jpeg`. 

![1.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/rQXxa3kXLcO_mrfRL5O2bg/1.png)

>Please note that if you encounter the error `FAILED Wait failed for application 'prodlist'`, you can rename the application to `prodlist1` and re-execute the command.

3. Deploy the microservice for Dealer Pricing, which provides API endpoints to retrieve dealer pricing information.

> Note: Please use the below parameters for the deploy command

**build-source** - `https://github.com/ibm-developer-skills-network/wzpvw-dealer_evaluation_backend_js.git`

**build-context-dir** - `dealer_details`

**port** - `8080`

**name** - `dealerdetails`

**image** -  `us.icr.io/${SN_ICR_NAMESPACE}/dealerdetails`

> Copy the deployment URL and save it in a notepad or other text editors.

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the successful deployment and name it `dealer_details_deploy.png` or `dealer_details_deploy.jpeg`.

![2.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/mJN5bSI-v7-v9mu0GcAU6A/2.png)

>Please note that if you encounter the error `FAILED Wait failed for application 'dealerdetails'`, you can rename the application to `dealerdetails1` and re-execute the command.

::page{title="Part B: Deploy the Dealer Evaluation Frontend Microservice"}

1. Open new terminal, go to the `/home/project` directory.

```
cd /home/project
```

2. Clone the repository https://github.com/ibm-developer-skills-network/pcsjq-dealer_evaluation_frontend_js.git in your /home/project directory.

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the successful git cloning and save it as `git_clone.png` or `git_clone.jpeg`.
![3.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/vlneePr3w29sVp1VtGtwTA/3.png)

3. Change to the `pcsjq-dealer_evaluation_frontend_js` directory.

4. Update the index.html file with the deployment URLs obtained from the microservice deployments. (`http://localhost:5000/` and `http://localhost:8080/`), copy the deployment URLs you copied in the appropriate location. Make sure you end the URLs with a `/`.

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the changes and save it as `index_urlchanges.png` or `index_urlchanges.jpeg`.

![4.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/rtIv9DbU-LIRk8ohHTM_FA/4.png)

5. Deploy the Dealer Evaluation frontend microservice by pointing the build-source to the current directory.

**build-source** - `.`

**port** - `5001`

**name** - `frontend`

**image** - `us.icr.io/${SN_ICR_NAMESPACE}/frontend`

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the successful deployment and name it `frontend_deploy.png` or `frontend_deploy.jpeg`.

![5 - frontend.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/QkJA-Rv_KjVVGyBFzsVeAg/5%20-%20frontend.png)

>Please note that if you encounter the error `FAILED Wait failed for application 'frontend'`, you can rename the application to `frontend1` and re-execute the command.

6. Click the link to load the homepage. Please note the page takes time to load the first time you access it.

7. Click the products drop down to see if the products have been populated.

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the home page showing the products list and name it `homepage.png` or `homepage.jpeg`.

![6.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/k1HMdU5fO98g4osiAVFyuw/6.png)

8. Choose a specific dealer for the product and verify that the price is displayed.

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the entire page showing the product chosen, and dealers that supply the listed product returned by the microservice and name it `product_dealer.png` or `product_dealer.jpeg`.

![7.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/JIzwNZLBPYIgNjSdY2LQRQ/7.png)

9. After the dealers dropdown populates, choose a particular dealer for the product and see if the price charged by that dealer is displayed.

> Allow 10 to 20 seconds to load the page.

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the entire page showing the product chosen, dealer chosen, and the price returned by the microservice and name it `product_dealer_price.png` or `product_dealer_price.jpeg`. 

![8.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/4dxIhV1_PCDKxwthrNcLWw/8.png)

10. Choose the `All Dealers` option for a product (make sure you choose a product that has more than one dealer). Pricing of all dealers offering the product should be shown on the screen.

**For Option 1 - AI Graded Submission and Evaluation** and **For Option 2 - Peer Graded Submission and Evaluation**: Take a screenshot of the entire page showing the product chosen, `All Dealers` option chosen, and the prices charged by all dealers returned by the microservice and name it `product_all_dealers_prices.png` or `product_all_dealers_prices.jpeg`.

![9.png](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/uPv039kSym3XtOjkz0RJuA/9.png)
::page{title="Checklist for submission"}

Follow the checklist below to verify that your project meets all requirements before submission.
	
**Submit your work through either Option 1: AI-Graded Submission and Evaluation or Option 2: Peer-Graded Submission and Evaluation, depending on the submission path you choose for project evaluation.**

Follow the submission checklist below if you are proceeding with **Option 1: AI-Graded Submission and Evaluation** and **Option 2: Peer-Graded Submission and Evaluation**:

##### Task 1:

Deploy the Microservice for Product Details and submit the screenshot of the successful deployment on Code Engine.

##### Task 2:

Deploy the Microservice for Dealer Pricing  and submit the  screenshot of the successful deployment on Code Engine.

##### Task 3:

Git clone the Dealer Evaluation (Frontend) Microservice from the provided Git URL and submit the screenshot of the cloned repository. 
##### Task 4:  

Change the code to point to the API endpoints in the placeholders, using the deployed URLs, and submit the screenshot of the code change in index.html.

##### Task 5:

Deploy the Dealer Evaluation Frontend Microservice and submit the screenshot of the successful deployment on Code Engine.

##### Task 6: 

Open the deployment link and submit the screenshot of the homepage showing the products preloaded in the dropdown.

##### Task7:

When a product is selected from the dropdown, the dealers supplying the product should be listed, Submit the screenshot of the same. 

##### Task 8:

When a dealer is selected for a product, the price offered by the dealer should be displayed, Submit thescreenshot of the same.

##### Task 9:
When all dealers are selected from the list, the price of all dealers offering the product should be displayed and Submit the screenshot of the same.
#### Congratulations! You have completed the final project!

## Summary:

In this lab, you\'ve successfully deployed multiple microservices to build an integrated application. This includes two backend microservices developed in JavaScript and Node.js, along with a front-end microservice.

## Author(s)

Alima Akhter

#### Other Contributor(s)

**[Rajashree Patil](https://www.linkedin.com/in/rajashree-patil-47263419b)**

<h3 align="center"> &#169; IBM Corporation. All rights reserved. <h3/>

<!--## Changelog

| Date | Version | Changed by | Change Description |
|------|--------|--------|---------|
| 28-02-2025 | 1.0  | Rajashree Patil | Initial version created |
| 17-03-2025 |  | Prashant Juyal | QA edits |
| 2025-07-15 | 1.2 | Sapthashree | Updated the title as per Rav's feedback |

<footer> 
<img align="left" src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-CD0210EN-Coursera/images/SNIBMfooter.png" alt=""> 
</footer> 
