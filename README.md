# Crawl Metadata of Max Planck Institutes

Set Up:

```sh
git clone https://github.com/dh-thesis/crawl.git
cd crawl/
virtualenv -p python3 --no-site-packages env
source env/bin/activate
pip install -r requirements.txt
deactivate
```

- make sure you have [Gecko Driver](https://github.com/mozilla/geckodriver/releases/) available on your `PATH`
- start crawling:

```sh
./main
```
## Scripts

The following scripts are used to crawl informations about the current Max Planck Institutes (MPIs), their research domains (`category`) and research areas (`tag`) from the website of the Max Planck Society.

- [`src/crawl_mpis_eng.py`](./src/crawl_mpis_eng.py)
- [`src/crawl_mpis_deu.py`](./src/crawl_mpis_deu.py)

Requirements: [Selenium](https://pypi.org/project/selenium/), [Firefox](https://www.mozilla.org/en-US/firefox/) and [Gecko Driver](https://github.com/mozilla/geckodriver/releases/)

### Mapping of MPIs to MPG.PuRe Entities

The following scripts can be used to map the crawled MPIs to their corresponding identifiers in MPG.PuRe and to find the associated contexts as well as categories and thematic tags of the institutes. (--> Important that you have done the [retrieval](https://github.com/dh-thesis/retrieve) before!)

- [`src/map_mpis_eng.py`](./src/map_mpis_eng.py)
- [`src/map_mpis_deu.py`](./src/map_mpis_deu.py)
- [`src/map_mpis.py`](./src/map_mpis.py)
- [`src/map_post.py`](./src/map_post.py)

Use these scripts (except `src/map_post.py`) by running:

```sh
./map
```

This will create a mapping (`mpis_ous.json`) from institutes to identifiers at path `../base/data/mpis/map/`. The mapping should be refined manually! Check if institutes not found have in fact corresponding identifiers in MPG.PuRe. After having done this you can run the post-mapping procedure:

```sh
source env/bin/activate
python -m src.map_post
```

Requirements: [Pybman](https://pypi.org/project/pybman/)
