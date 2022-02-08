Solr Prometheus Exporter
========================

Directory structure
-------------------
```solr_exporter/exporter/
├── README.txt
├── bin
│   ├── solr-exporter
├── conf
│   ├── grafana-solr-dashboard.json
│   ├── log4j.properties
│   └── solr-exporter-config.xml
├── dist __moved as mentioned in item 2 below__
├── lib
└── lucene-libs
```


1. The solr exporter can be found in a [solr-7.3.1 binary distribution](https://archive.apache.org/dist/lucene/solr/7.3.1/solr-7.3.1.tgz) at `${BASE_DIR}/solr-7.3.1/contrib/prometheus-exporter`. Or, if you're in the mood to type, in a riak build tree after `make rel` in `${BUILD_DIR}/riak/_build/rel/lib/yokozuna/build/solr-7.3.1/contrib/prometheus-exporter`.

2. Besides the `prometheus-exporter` directory the exporter also requires the `dist` directory in the top-level `solr-7.3.1` directory. That directory's jars are referenced in `solr-exporter` via `../../dist`. In order to avoid placing additional full solr distributions[^1] on the riak machines the `dist` directory is moved from `solr-7.3.1/dist` to `${EXPORTER}/dist` and the `solr-exporter` script is edited to point to the new location.

3. Configuration information can be found on the [solr
   website](https://solr.apache.org/guide/7_3/monitoring-solr-with-prometheus-and-grafana.html).

[^1]: Distributions we are likely to forget about when the next vulnerability rolls around.
