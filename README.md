# foreign-country-viewer
Repository for deploying the "How Foreign will New Countries Feel?" viewer app. Exploratory data analysis resources have been moved to their own sub-folder. 

Because python notebooks contain visualizations of the world map generated with the Folium library, they may be too graphically intense for GitHub to render an output for all notebooks.

## Link to the app itself:
[Viewer](https://foreign-country-viewer.herokuapp.com/app/1)

## Limitations:
It is inherently difficult to quantify how foreign a country will "feel", nevertheless that is this project's lofty goal. To try and achieve this, users are able to customize the results by adjusting the relative weights of six different "axis" (Demographics, Health, Climate, Economy, Language, and Religion). This way the algorithm can put a greater or lesser emphasis on each of these factors depending on how much the user believes they contribute to the "feel" of a place for them. For a granular view of what data is used to build the groups for each axis, check out the data sources.

The algorithm works by using different clustering algorithms to group countries that share similarities. Countries can be similar in many ways, and there are varying degrees to which countries can be similar, so this analysis uses 36 different clustering algorithms that group countries in 36 different ways. The exact way in which each of these clusters works was the subject of a great deal of tuning. To compute how similar any two countries are, all the viewer app has to do is find how many times a given country appears in the same group as another.

Each clustering algorithm only sees data relating to one of the six axis. This allows the relative weights of each axis to be factored into the algorithm after all of the computationally intensive clustering has been done. This, in turn, greatly increases the performance of the wed app (which is already very slow due to the time it takes to render the map). For each of the six axis, six sets of groups are generated, which is why there is a total of 36 sets of groups.

## Data Sources:
Yes... the data was all scrubbed from Wikipedia. It may not be the most reliable, but of all the different data sources I could find, it did have the most consistent naming conventions, and when you are trying to aggregate data about this many different kinds of factors, that ends up being the most important thing. Below are links to the specific data sources.

### Demographics Data
* [Age Structure](https://en.wikipedia.org/wiki/List_of_countries_by_age_structure)
* [Population and Population Density](https://en.wikipedia.org/wiki/List_of_countries_and_dependencies_by_population_density)
* [Fertility Rate](https://en.wikipedia.org/wiki/List_of_countries_by_past_fertility_rate)
* [Sex Ratio](https://en.wikipedia.org/wiki/List_of_countries_by_sex_ratio)

### Health Data
* [Suicide Rate](https://en.wikipedia.org/wiki/List_of_countries_by_suicide_rate)
* [Maternal Mortality Rate](https://en.wikipedia.org/wiki/List_of_countries_by_maternal_mortality_ratio)
* [Child Mortality Rate](https://en.wikipedia.org/wiki/List_of_countries_by_infant_and_under-five_mortality_rates)
* [Obisety Rate](https://en.wikipedia.org/wiki/List_of_countries_by_obesity_rate)
* [Homicide Rate](https://en.wikipedia.org/wiki/List_of_countries_by_intentional_homicide_rate)
* [Life Expectancy](https://en.wikipedia.org/wiki/List_of_countries_by_life_expectancy)

### Climate Data
* [Average Annula Tempature](https://en.wikipedia.org/wiki/List_of_countries_by_average_yearly_temperature)
* [Average Annual Rainfal](https://en.wikipedia.org/wiki/List_of_countries_by_average_annual_precipitation)
* [Latitude of Population Centers](https://en.wikipedia.org/wiki/List_of_national_capitals_by_latitude)
* [Land Area](https://simple.wikipedia.org/wiki/List_of_countries_by_area)
* [Forest Area](https://en.wikipedia.org/wiki/List_of_countries_by_forest_area)
* [Coastline Distance](https://en.wikipedia.org/wiki/List_of_countries_by_length_of_coastline)
* [Urbanization](https://en.wikipedia.org/wiki/Urbanization_by_country)

### Economy Data
* [GDP Composition by Economic Sector](https://en.wikipedia.org/wiki/List_of_countries_by_GDP_sector_composition)
* [Total GDP (PPP)](https://en.wikipedia.org/wiki/List_of_countries_by_GDP)
* [Poverty Rate](https://en.wikipedia.org/wiki/List_of_countries_by_percentage_of_population_living_in_poverty)
* [Human Development Index](https://en.wikipedia.org/wiki/List_of_countries_by_Human_Development_Index)
* [Wealth Inequality](https://en.wikipedia.org/wiki/List_of_countries_by_wealth_per_adult)

### Language Data
* [List of World Languages](https://en.wikipedia.org/wiki/List_of_languages_by_number_of_native_speakers)
* [Languages Spoken by Country](https://en.wikipedia.org/wiki/List_of_official_languages_by_country_and_territory)
* [Percent of English Speakers](https://en.wikipedia.org/wiki/List_of_countries_by_English-speaking_population)

### Religion Data
* [Major World Religions](https://en.wikipedia.org/wiki/Religions_by_country)
* [Catholicism](https://en.wikipedia.org/wiki/Catholic_Church_by_country)
* [Eastern Orthodoxy](https://en.wikipedia.org/wiki/Eastern_Orthodoxy_by_country)
