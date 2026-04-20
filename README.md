# Pricing OPS RO Tariff

This is my writeup of the Pricing OPS project assigned to me by Giorgi. The aim of the project is to update our PCW tariffs with ```effective_from_date```$\leq$ 01/04/2026 with their RO counterparts. 

## Tariff Counts

To make my job easier, I wanted to count the number of supply fids we have for each Tariff type affected by RO (which include Dual Rate Fixed and Single Rate Fixed Tariffs, for electricity imports only). I got this plot 

<img width="1217" height="686" alt="image" src="https://github.com/user-attachments/assets/45b2ad81-b3e6-4311-9586-a8148c264dae" />

from the following logic:

<img width="1146" height="680" alt="image" src="https://github.com/user-attachments/assets/c36050eb-d648-44bd-8dd5-a7af9b61e21d" />

As the counts are non-zero we will have to adjust each tariff for each tarrif type in order to take into account the RO deductions. Note that this plot defintely overcounts as I did not filter in order to remove duplicate supply fids - for example, one supply fid may have multiple rows of tariff info. Regardless, it atleast informed me that there were no tariffs with zero active supply fids. 

To collect the Tarriff info itself such as unit rates, standing charges, etc, I simply joined ```Ro Tariff Mapping``` with ```Tariff Rate``` and ```Tariff given that the Tariff ID's match. This then me a breakdown of the all the necessary info for tariffs with RFIDS. I then sperately joined ```Ro Tariff Mapping``` with ```Tariff Rate``` for the necessary general info. This was used as we can fill the forms with data taken from the sum of the JSON files included in this table. These JSON's includes entries like "metering", "unit rate", "government subsidies", etc. 
