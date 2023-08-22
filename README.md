# NN_satellite_state_vec_Corrector_
## TLE-to-state vector SGP4 model corrector via neural network according ILRS cpf predictions
## ABOUT:
The project is dedicated to the problem of improving accuracy satellite's state vector evaluation from TLE (two-line-element) parameters. There are several models such as SGP4 and SGP8, available to determine satellite's state vector [x,y,z] from TLE with some errors up to 500 m that maybe to significant in some critical cases for spacecraft's safety.
ILRS data from ground stations provide very accurate state vectors evaluation with negligible error up to several cm. The main problem is that these data can be avaluated only for several satellites and during visible time zones for ground stations. In that case TLE date is more universal and stable, as it's regularly generated for each active satellite with norad id.
Our approach consisits of making SGP4 model more accurate using ILRS state vectors on the same timestamps as the gt (ground truth) coordinates [x,y,z] for the spacecraft. As the CRS (coordinate reference system) we use all calculations on J2000 as one of hte most universal inertial (fixed) CRSs.
We compare the rusults of the classic ML models corrections to SGP4 model such as Random Forest etc. with neural networks (MLP with several hidden layers) results to find the most siutable architecture for such roblem of SGP correction according ILRS gt data.
## USAGE INSTRUCTIONS:

## First, install all required Python packages that are provided in requiremints.txt file in this repo!

To setup all this libs just run this commnd in your terminal or code cell:

- `!pip install -r requirements.txt`
- 
Here we use ILRS and TLE data during 2021-2022 period. All ILRS CPF predict can be downloaded for free from:
- https://urs.earthdata.nasa.gov/oauth/authorize?client_id=gDQnv1IO0j9O2xXdwS8KMQ&response_type=code&redirect_uri=https%3A%2F%2Fcddis.nasa.gov%2Fproxyauth&state=aHR0cDovL2NkZGlzLm5hc2EuZ292L2FyY2hpdmUvc2xyL2NwZl9wcmVkaWN0cy8yMDIwL2dsb25hc3MxMDUv

All ILRS CPF predict can be downloaded for free from:
- https://celestrak.org/
- https://www.space-track.org/auth/login
(All these sources require registration in advance)

As the experimental satellites we chose **Glonass-105, TandemX and Terrasar**. TLE and ILRS data for 2021-2022 can be found in this repository in  `tle` and `cpf_predicts` folders respectively. TLE data for these satellites and time period can stored in **3_LEO_df_TLE_2021_2022.csv** in this repository for more comfortable processing it.

All needed code for fitting and testing models on these data can be found in **SGP_ILRS_data_corrector.ipynb** notebook as well as the code cells with MLP and classical ML RandomForest model accurateness comparison and state vectors plots in `J2000` CRS.

You can also get TLE data for any needed active satellite and time period using `def get_tle_from_spacetrack()` function in the **SGP_ILRS_data_corrector.ipynb** notebook, using your login and password in the arguments of this function.

In the end of **SGP_ILRS_data_corrector.ipynb** notebook You can modify plots and training pipelines as well as used models for TLE corrections and make your own research to impove result that we provide!

## Contacts
You can leave all your questios, offers and commnets to Belyakov Nikita on E-mail or Telegram:
- MSUBelyakovNV@yandex.ru
- @workout2018
