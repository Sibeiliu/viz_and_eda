EDA
================
Jeff Goldsmith
10/3/2019

## create the weather data

``` r
weather_df = 
  rnoaa::meteo_pull_monitors(c("USW00094728", "USC00519397", "USS0023B17S"),
                      var = c("PRCP", "TMIN", "TMAX"), 
                      date_min = "2017-01-01",
                      date_max = "2017-12-31") %>%
  mutate(
    name = recode(id, USW00094728 = "CentralPark_NY", 
                      USC00519397 = "Waikiki_HA",
                      USS0023B17S = "Waterhole_WA"),
    tmin = tmin / 10,
    tmax = tmax / 10,
    month = lubridate::floor_date(date, unit = "month")) %>%
  select(name, id, date, month, everything())
```

    ## Registered S3 method overwritten by 'crul':
    ##   method                 from
    ##   as.character.form_file httr

    ## Registered S3 method overwritten by 'hoardr':
    ##   method           from
    ##   print.cache_info httr

    ## file path:          /Users/jeffgoldsmith/Library/Caches/rnoaa/ghcnd/USW00094728.dly

    ## file last updated:  2018-06-14 13:08:48

    ## file min/max dates: 1869-01-01 / 2018-06-30

    ## file path:          /Users/jeffgoldsmith/Library/Caches/rnoaa/ghcnd/USC00519397.dly

    ## file last updated:  2018-06-14 13:09:00

    ## file min/max dates: 1965-01-01 / 2018-06-30

    ## file path:          /Users/jeffgoldsmith/Library/Caches/rnoaa/ghcnd/USS0023B17S.dly

    ## file last updated:  2018-06-14 13:09:04

    ## file min/max dates: 1999-09-01 / 2018-06-30
