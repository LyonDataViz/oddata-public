# oddata-public

Repository for origin-destination datasets

1. Create a directory with you `your-project` name

2. Create a `your-project.json` file that describes your projet (see examples in other directories)

3. Format your dataset into a CSV file, add link to this dataset in `your-project.json`

4. Add link to `your-project` directory in the master file `dataset.json` (list of all datasets)

5. Your dataset should appear in https://observablehq.com/d/188f3eb2bb17b279

## The file [dataset.json](dataset.json) links to all those datasets

* Each directory contains a dataset
* A ```.json``` files in each of those directory describes the dataset (attributes, ..)
* A ```.csv``` file contains the raw data

You may online change the ```dataset.json``` **once**.

## Format of the ```.csv``` file
*This file is a classical CSV file, preferably with commas (`,`) as separator. Each line represents one O/D trajectory. The column names are referenced in the data.json file.*

Example (from [random/random-data.csv](random/random-data.csv):

```{csv}
time,group,x1,x2,y1,y2,group_x1,group_x2,group_y1,group_y2,distance,distance_category,orientation,hour,minute,second,year,month,day
Mon Jan  1 20:56:01 2018,2,752,542,899,30,3,2,0,4,894.0139819935704,long,S,20,56,1,2018,1,1
Mon Jan  1 21:41:05 2018,0,677,418,886,186,3,2,0,4,746.3785902610015,long,S,21,41,5,2018,1,1
Mon Jan  1 06:28:10 2018,2,225,380,53,562,1,1,4,2,532.0770620878145,medium,N,6,28,10,2018,1,1
```

## Format of the data.json file
*This data describes the attributes (columns) of the .csv file.*

Complete example:

```{javascript}
{
  "file": "random/random-data.csv",
  "name": "Random XY Data",
  "header": 1,
  "separator": ",",
  "meta": {
    "date": "start_time",
    "group": "group",
    "timeParse": "%c",
    "cumul": "distance"
  },
  "grids": [
    {
      "title": "random",
      "tree": [
        { "group": "orientation", "gridding": "grid", "padding": 5 },
        { "group": "start_time" }
      ]
    },
    {
      "title": "random-od",
      "tree": [
        {
          "group": "cell_group_destination",
          "gridding": "grid",
          "padding": 5
        },
        {
          "group": "start_time"
        }
      ]
    },
    {
      "title": "random-group-color",
      "tree": [
        { "group": "orientation", "gridding": "grid", "padding": 5 },
        { "group": "group", "gridding": "grid", "padding": 5 },
        { "group": "group" }
      ]
    }    
  ],
  "attributes": [
    {
      "name": "x1",
      "type": "quantitative"
    },
    {
      "name": "x2",
      "type": "quantitative"
    },
    {
      "name": "y1",
      "type": "quantitative"
    },
    {
      "name": "y2",
      "type": "quantitative"
    },
    {
      "name": "distance",
      "type": "quantitative"
    },
    {
      "name": "distance_category",
      "type": "categorical"
    },
    {
      "name": "orientation_4",
      "type": "categorical"
    },
    {
      "name": "start_time",
      "type": "categorical"
    },
    {
      "name": "start_year",
      "type": "categorical"
    },
    {
      "name": "start_month",
      "type": "categorical"
    },
    {
      "name": "start_day",
      "type": "categorical"
    },
    {
      "name": "start_hour",
      "type": "categorical"
    },
    {
      "name": "start_minute",
      "type": "categorical"
    },
    {
      "name": "start_second",
      "type": "categorical"
    },
    {
      "name": "end_time",
      "type": "categorical"
    },
    {
      "name": "end_year",
      "type": "categorical"
    },
    {
      "name": "end_month",
      "type": "categorical"
    },
    {
      "name": "end_day",
      "type": "categorical"
    },
    {
      "name": "end_hour",
      "type": "categorical"
    },
    {
      "name": "end_minute",
      "type": "categorical"
    },
    {
      "name": "end_second",
      "type": "categorical"
    },
    {
      "name": "duration",
      "type": "quantitative"
    },
    {
      "name": "speed",
      "type": "quantitative"
    },
    {
      "name": "speed_category",
      "type": "categorical"
    },
    {
      "name": "orientation_8",
      "type": "categorical"
    },
    {
      "name": "duration_category",
      "type": "categorical"
    },
    {
      "name": "cell_group_origin",
      "type": "categorical"
    },
    {
      "name": "cell_group_destination",
      "type": "categorical"
    },
    {
      "name": "bi_start_time",
      "type": "categorical"
    },
    {
      "name": "bi_start_year",
      "type": "categorical"
    },
    {
      "name": "bi_start_month",
      "type": "categorical"
    },
    {
      "name": "bi_start_day",
      "type": "categorical"
    },
    {
      "name": "bi_start_hour",
      "type": "categorical"
    },
    {
      "name": "bi_start_minute",
      "type": "categorical"
    },
    {
      "name": "bi_start_second",
      "type": "categorical"
    }
  ],
  "author": "Romain Vuillemot",
  "description": "Random data",
  "source": ""
}
```

The `meta` object describes the well-known data fields: origin and destination's coordinates, dates, groups…

The `attributes` object describes the secondary fields: duration, price, age… that will be used to color maps or for statistical analysis.

*Dates* must be formatted in a way that moment.js can parse. It is possible to specify the date format as a `dateformat` attribute.

*Separator* is, by default, the comma ",". It is passed to d3.dsv.

*Header* is unused (yet).

*Author* is the author or maintainer of the dataset.

*Description* describes the dataset.

*Source* is the source of the dataset.

## Usage

[This Observable notebook](https://observablehq.com/d/188f3eb2bb17b279) shows how to use this set of datasets in a unified manner.
