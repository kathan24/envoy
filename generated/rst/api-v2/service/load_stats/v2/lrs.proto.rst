.. _envoy_api_file_envoy/service/load_stats/v2/lrs.proto:

Load reporting service (LRS)
============================


.. _envoy_api_msg_service.load_stats.v2.LoadReportingService:

LRS is an Envoy API to emit load report. Envoy will initiate a StreamLoadStats bidi stream with a management server.
Once the connection is established, management server can send a LoadStatsResponse to a cluster. Envoys in this cluster
will aggregate the stats and will send the report in LoadStatsRequests. This is done periodically based on the frequency
mentioned in the LoadStatsResponse.

service.load_stats.v2.LoadStatsResponse
---------------------------------------

`[service.load_stats.v2.LoadStatsResponse proto] <https://github.com/envoyproxy/envoy/blob/3d162074fca24448334e18fb2fa507ffd7819e7e/api/envoy/service/load_stats/v2/lrs.proto#L65>`_

.. code-block:: json
  {
    "clusters": [],
    "load_reporting_interval": "...",
    "report_endpoint_granularity": "..."
  }

.. _envoy_api_field_service.load_stats.v2.LoadStatsResponse.clusters:

clusters
  A list of upstream clusters you want to get stats for.


.. _envoy_api_field_service.load_stats.v2.LoadStatsResponse.load_reporting_interval:

load_reporting_interval
  The minimum interval of time to collect stats over


.. _envoy_api_field_service.load_stats.v2.LoadStatsResponse.report_endpoint_granularity:

report_endpoint_granularity
  Set to *true* to get endpoint level stats


service.load_stats.v2.LoadStatsRequest
--------------------------------------

`[service.load_stats.v2.LoadStatsRequest proto] <https://github.com/envoyproxy/envoy/blob/3d162074fca24448334e18fb2fa507ffd7819e7e/api/envoy/service/load_stats/v2/lrs.proto#L54>`_

.. code-block:: json
  {
    "node": "{...}",
    "cluster_stats": []
  }

.. _envoy_api_field_service.load_stats.v2.LoadStatsRequest.node:

node
  (:ref:`core.Node <envoy_api_msg_core.Node>`) The node sending stats over the stream.


.. _envoy_api_field_service.load_stats.v2.LoadStatsRequest.cluster_stats:

cluster_stats
  `[api.v2.endpoint.ClusterStats proto] <https://github.com/envoyproxy/envoy/blob/3d162074fca24448334e18fb2fa507ffd7819e7e/api/envoy/api/v2/endpoint/load_report.proto#L117>`__
  A list of stats for each upstream cluster
