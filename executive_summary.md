# World Data League 2023

## 🎯 Challenge
Determining the mobility flow in the city of Lisbon based on mobile phone data

## Team Name
Mo Money, Mo Models


## 👥 Authors
* David Raposo
* Duarte Pereira
* Martim Chaves
* Paulo Sousa


## ✨ Introduction (250 words max)

The problem that the CNN-LSTM model is aiming to solve is the issue of overcrowding in public spaces within the city of Lisbon. The growing population in the metropolitan area of Lisbon, which is estimated to be 3,001,000 in 2023 [1], poses a significant challenge for city managers to ensure public safety and comfort. This high population density can lead to overcrowding in public spaces such as public transportation, parks, and shopping centers. Overcrowding can cause discomfort and inconvenience for individuals and, in extreme cases, lead to safety hazards such as stampedes and accidents.

This trend is not limited to the city of Lisbon. According to an Harvard International Review Article [2], the global population is currently rising at a steady rate. Between the years 1800 and 2023, the population of Earth has increased significantly. In 1800, it was estimated that there were around 1 billion inhabitants, and by 1940, this number had risen to 2.3 billion. Over the next three decades, the population continued to grow rapidly, reaching 3.7 billion by 1970. As of 2023, the world's population is approximately 7.8 billion, showing the most significant increase in the Earth's population in the last five decades.

With this in mind, it is vital to provide city managers with tools to detect and prevent overcrowding events.

**References:**

[1] https://www.macrotrends.net/cities/22167/lisbon/population#:~:text=The%20current%20metro%20area%20population,a%200.51%25%20increase%20from%202020. - last accessed 18/04/2023

[2] https://hir.harvard.edu/public-health-and-overpopulation/ - last accessed 18/04/2023


## 🔢 Data (250 words max)

We used the datasets, provided by the WDL, regarding mobile devices.
With this data we created a grid map. For the grid cells where there was a train line or station a new identifier was added. These data were taken from the Lisboa Aberta portal [2].

We also explored climate data briefly - nominally precipitation and temperature - using climatelab to load the ERA5 reanalysis dataset [1], but we could only obtain one value for the entire city per hour, so we did not consider it a priority at the moment.

One of the datasets provided by the WDL that initially looked promising was the traffic conditions. However as this data were not real-time it were not relevant as inputs to the model. In the future it could be used to seek an explanation for certain phenomena observed by the data

In order to improve the quality of the data it would be interesting to standardise the type of files with the available data, as some are in .csv format and others in .xlsx. Also .geojson data has been used.

Finally, we noticed that the data from mobile devices had maxima much higher than the 99th percentile, which indicated that they were erroneous measurements. 


**References:**

[1] https://cds.climate.copernicus.eu/
[2] https://lisboaaberta.cm-lisboa.pt/



## 🧮 Methods and Techniques (250 words max)

TODO - EDA

The proposed CNN-LSTM architecture joins state-of-the-art deep learning models for image processing (CNN, Convolutional Neural Network) and time series forecasting (LSTM, Long Short-Term Memory). In theory, this model is able to leverage the spatial relationships within the city grid to provide better predictions based on neighbor relations, as well as the temporal dimension for forecasting. However, we encountered some challenges with training time that limited performance, and had to limit the learning rate, epochs, and batch size. We also had to follow a preliminar preprocessing pipeline, as we were performing EDA in parallel. Future work must focus on improving the experimental infrastructure, model architecture, integrating new data, and the preprocessing suggested in the EDA stage.

The transport data have been superimposed on the grid created earlier. For this it was necessary to find out the distance from each of the stations to the centroids of the grid cells. Then this grid was ordered and the cell with the shortest distance was the one most likely to have a station. 	


## TODO - 💡 Main Insights (300 words max)
Explain what you discovered from addressing this problem, such as interesting facts or statistics.

EDA insights
errors
Model
performance
train time limitations

## TODO - 🛠️ Product
In this section you should define the product that can be created by using the model developed. Make sure that the product solves the problem in a holistic way, takes into account the constraints of the topic entities (specifically mention these constraints).
### Definition
Define in **one sentence** what product(s) could be built out of the code you produced.
A dashboard that assists in public transport planning, and a dashboard that assists in policing.


### Users
Describe who would be the users of your product and for what purpose would they use it.
Example: Traffic controllers use the dashboard during their work to better plan where to dispatch resources

Decision makers in transport companies, especially metro and rail, can use our dashboard and the forecasts our models provide to decide the human resources deployed for each moment of the day.
City councils can also use the predictions from our models to decide which events to promote in which part of town to promote a more dispersed population and thus a better quality of life for citizens.
The citizens of the city in general can also benefit from our predictions, in order to have a lifestyle more in tune with their personality. They can move to more crowded areas or to quieter areas, as they wish.
Traffic police can also perform better at resolving overcrowding situations preemptively, and ensure citizens’ safety.

### Activities

Predicts the most likely locations for overcrowding situations

### Output
Population density predictions on a map for the next X hours.

###  Scalability

For this solution to be employed in another environment, we would require it to have similar phone grid history. Additional data such as tranports and climate could also be helpful to improve model performance. Finally, a larger model following our pipeline and trained with data from more locations could have more generalization capabilities.

## TODO - 🌍 Social Impact Measurement
This section will help to guide you on how to measure the impact of your product. Make sure that measurement is thoroughly quantitative, even if you need to estimate some of the numbers.
### Outcome
To predict overcrowding situations and decrease response time so that cities are more secure and provide better quality of life for its citizens.


### Impact Metrics
Average REsponse Time from Transportation Planning
Average Response Time From Police Stations


### TODO - Impact Measurement
Since you cannot wait to see the impact of your product, estimate it. You can do that by either using the estimations/predictions of your model, market research, products from proxy industries and/or similar locations, etc.


Example:
* *Based on model predictions*: Our model estimates a decrease of 6 minutes of the average dispatch time and a decrease of the average distance of 200 metres
* **THIS!! NO EXTRAPOLATION REQUIRED, JUST REFERENCE** *Based on proxy products*: Similar studies in other cities show that the dispatch time can be decreased by as much as 13 minutes, depending on the traffic intensity of that city.

