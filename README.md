# Snowpark-Python-CitiBike-ML  
_By: David Stearns_

### Introduction  
This repository holds code for a quick and easy demo for **Snowpark Python**. Set up is easy and requires very little configuration. You should be up and running in 5 minutes, and be able to run through the entire demo in 10 minutes. This demo covers the entire gamut of the machine learning pipeline; everything from feature engineering, model creation, model training, and model deployment. Within this, I cover creation of a **Stored Procedure for model training** and a **Scalar UDF for model deployment**.  
  
_A little bit about the mechanics at play here:_  
A **Scalar UDF** is a function that can receive a scalar input, meaning, it can receive only one row (_1D Array_) and output only one row. You can see here how a Scalar UDF would fail to perform when the scenario necessitates multi-row computation. The function created in this demo is a Scalar UDF and it is to be used for point predictions. A **Vectorized UDF** is on the way, but TBA. The Vectorized UDF can receive entire series and/or a data frame to run computation on and output a series which can be broken down into multiple rows. When comparing multi-row computation performance between Scalar UDF's and Vectorized UDF's, Vectorized UDF's see about a 95-97% increase in performance (based on time to execute). Additionally, using the Vectorized UDF's will contribute to cost savings in line with the total time of execution.  
  
Regarding the **Stored Procedure**, standard warehouses allocate 5GiB RAM to the Snowpark environment. The Stored Procedure is how we accomplish the model training in Snowflake. With the advent of **High Memory Warehouses**, we will be getting memory slots upwards of 256GiB. The initial offering appears to be only 256GiB (as of 7/27/22, and this will change), **and the Snowpark environment will receive 80GiB RAM**. It is important to note that the memory allocation for the Snowpark environment is not the entire memory slot of the warehouse. There are developments coming that will unlock 90% of the memory available for Snowpark. This is TBA.  
  
