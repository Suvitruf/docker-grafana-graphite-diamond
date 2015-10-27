StatsD + Graphite + Grafana + Diamond
---------------------------------------------

This image contains default configuration of StatsD, Graphite and Grafana, and comes with [Diamond](https://github.com/BrightcoveOS/Diamond) to collect system metrics.

The container exposes the following ports:

- `80`: the Grafana web interface.
- `8125`: the StatsD port.
- `8126`: the StatsD administrative port.
- `2003`: graphite port for plaintext.
- `2004`: port to Carbon’s pickle receiver.

### Building the image yourself ###
To build container just run `build` script.

To start a container with this image you just need to run `start` script.

Sometimes you need to start `init.sh` script to `dos2unix` all bash scripts needed.

For now short server name passing as argument to docker container. You can change it in `start` script.


### Using the Dashboards ###

Once your container is running all you need to do is:
- open your browser pointing to the host/port you just published
- login with the default username (admin) and password (admin)
- configure a new datasource to point at the Graphite metric data (URL - http://localhost:8000) with enabled proxy option and replace the default Grafana test datasource for your graphs

As default you have one dashboard with some system metrics. You can add new if you want.
![System metrics](https://cloud.githubusercontent.com/assets/1946939/10747065/3301174e-7c62-11e5-9c76-02c6d1ac8134.png)

### Collect more system metrics with Diamond ###

You can enable different [Handlers](https://github.com/python-diamond/Diamond/wiki/Handlers) and [Collectors](https://github.com/python-diamond/Diamond/wiki/Collectors). By default enabled only: CPUCollector, DiskSpaceCollector, DiskUsageCollector, LoadAverageCollector, MemoryCollector, UptimeCollector. 

Edit config file `./diamond/diamond.conf` if you need more metrics.
