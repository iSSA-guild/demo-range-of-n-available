
# Targets Amt Issa

## Data setup

``` r
library(amt)
library(sf)
library(stars)

data("amt_fisher", package = 'amt')
data("amt_fisher_covar", package = 'amt')


fisher <- st_as_sf(amt_fisher, coords = c('x_', 'y_'), crs = 31467, remove = FALSE)
lc <- st_as_stars(amt_fisher_covar$landuse)
elev <- st_as_stars(amt_fisher_covar$elevation)
popdens <- st_as_stars(amt_fisher_covar$popden)

crs <- st_crs(4326)

st_write(st_transform(fisher, crs), 'input/amt_fisher_locs_4326.gpkg')
write_stars(st_transform_proj(lc, crs), 'input/amt_fisher_lc_4326.tif')
write_stars(st_transform_proj(elev, crs), 'input/amt_fisher_elev_4326.tif')
write_stars(st_transform_proj(popdens, crs), 'input/amt_fisher_popdens_4326.tif')
```
