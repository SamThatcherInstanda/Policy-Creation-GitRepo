Dummy Test Data Collection
Overview

This Bruno collection creates policies populated with dummy test data using the Package API and Function App. It helps reduce the time spent creating policies through the on a published site, so testing can start sooner.

Environments

The collection has two environments: Test and Regression. Select the one that matches the environment you want to test.

Running the Collection

1. Hover over the collection name in Bruno.
2. Click the three-dot menu and select Run.
3. Choose the transaction types you want to create.
4. Set the number of policies to create by specifying the number of iterations.


Variables and Manual Configuration

Most variables are configured at the environment level, so you generally won’t need to change the requests themselves. There are two exceptions:

- StartRenewal: The StartDate must be set manually in the request parameters. I haven’t yet been able to add a year to PolicyStartDate with JavaScript, as I have for the other variables.

- Create MTA Quote: Set EffectiveChangeDate manually in the request body. Automating this is still in progress.

Generated Data

When you send the Generate Dummy Data request, its response is captured as a JSON object and used by subsequent requests.

The policy number increments with each request. After generating the data, you can edit the start and end date variables—for example, to test automatic renewals.

Limitations and Troubleshooting

- Create NB does not run calculations. It uses the CreateQuoteOrPolicyData method from the Package API, so referrals and declines are not triggered.

- The MTA and Renewal requests may return an HTTP 400 response due to an issue with the Package API. In most cases, the MTA or Renewal quote will still have started. Check the web application or database for the policy number to confirm.

Reusing the Collection

You’re welcome to fork the collection to your own machine and adapt it for your testing needs.

The collection can also be used with Postman, but its JavaScript variables use Bruno-specific references. Some additional configuration may therefore be needed.
