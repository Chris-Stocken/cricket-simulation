# Cricket MCMC Simulation Project

## Overview

This R script performs a Bayesian analysis on cricket data using Markov Chain Monte Carlo (MCMC) methods. The analysis includes fitting prior distributions, determining empirical prior distributions, calculating the posterior, and running MCMC simulations.

## Table of Contents

1. [Requirements](#dependencies)
2. [Parameter of Interest](#parameter-of-interest)
3. [Data Input](#data-input)
4. [Determining Prior Distributions](#determining-prior-distributions)
5. [Posterior Calculation](#posterior-calculation)
6. [Target Function](#target-function)
7. [MCMC Simulation](#mcmc-simulation)
8. [Diagnostics](#diagnostics)

## Requirements

The script requires the following R packages:
- rmarkdown
- knitr
- readxl
- moments
- corrplot
- pso
- psych
- GPArotation
- lavaan
- MASS

## Data Input

The script reads cricket data from CSV files containing the data from all International T20 cricket matches played in each year from 2007 to 2021.

## Research Question:
  Can the number of runs in a T20 cricket match be predicted based on prior data from previous cricket matches?
  
## Parameter of Interest:
  The likelihood function we are using is a gamma distribution and the parameters of interest are alpha and lambda that we are using to model the number of runs that are scored in a cricket innings. 


## Determining Prior Distributions
  Decided to use prior gammas for alpha and lambda because of the scale (values greater than 0) of the prior alphas and lambdas, each with their own hyperparameters of alpha and lambda, then fit these to find the values of the hyperparameters using maximum likelihood estimation provided by fitdistr() function.

## Target Function
  The target function for the Markov chain Monte-carlo was the posterior distribution found by multiplying the prior distributions with the likelihood function which takes into account the current data. To avoid issues when calculating the ratio between current and proposed values for alpha and lambda I decided to take the log-likelihood and log priors to get a log posterior.

## MCMC Simulation
  The Random Walk Metropolis Hastings algorithm was used to calculate the fitting values for alpha and lambda, this is repeated 500,000 times updating an alpha and lambda each time.

## Diagnostics
  This script also contains resulting diagnostics for the simulation including acf plots and cumulative mean plots for alpha and lambda



