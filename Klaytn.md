{
    "annotations": {
      "list": [
        {
          "builtIn": 1,
          "datasource": {
            "type": "datasource",
            "uid": "grafana"
          },
          "enable": true,
          "hide": true,
          "iconColor": "rgba(0, 211, 255, 1)",
          "name": "Annotations & Alerts",
          "target": {
            "limit": 100,
            "matchAny": false,
            "tags": [],
            "type": "dashboard"
          },
          "type": "dashboard"
        }
      ]
    },
    "description": "",
    "editable": true,
    "fiscalYearStartMonth": 0,
    "graphTooltip": 0,
    "id": 1,
    "iteration": 1653102893483,
    "links": [],
    "liveNow": false,
    "panels": [
      {
        "collapsed": false,
        "datasource": {
          "type": "prometheus",
          "uid": "USbDNXl7z"
        },
        "gridPos": {
          "h": 1,
          "w": 24,
          "x": 0,
          "y": 0
        },
        "id": 8,
        "panels": [],
        "title": "Klaytn Node Monitoring",
        "type": "row"
      },
      {
        "datasource": {
          "type": "prometheus",
          "uid": "USbDNXl7z"
        },
        "fieldConfig": {
          "defaults": {
            "color": {
              "mode": "thresholds"
            },
            "custom": {
              "align": "auto",
              "displayMode": "auto",
              "inspect": false
            },
            "mappings": [
              {
                "options": {
                  "0": {
                    "color": "red",
                    "index": 1,
                    "text": "not online"
                  },
                  "1": {
                    "color": "green",
                    "index": 0,
                    "text": "online"
                  }
                },
                "type": "value"
              }
            ],
            "thresholds": {
              "mode": "absolute",
              "steps": [
                {
                  "color": "green",
                  "value": null
                },
                {
                  "color": "red",
                  "value": 80
                }
              ]
            }
          },
          "overrides": []
        },
        "gridPos": {
          "h": 10,
          "w": 24,
          "x": 0,
          "y": 1
        },
        "id": 14,
        "options": {
          "footer": {
            "fields": "",
            "reducer": [
              "sum"
            ],
            "show": false
          },
          "showHeader": true,
          "sortBy": [
            {
              "desc": true,
              "displayName": "Value"
            }
          ]
        },
        "pluginVersion": "8.5.2",
        "targets": [
          {
            "datasource": {
              "type": "prometheus",
              "uid": "USbDNXl7z"
            },
            "editorMode": "code",
            "exemplar": false,
            "expr": "up{job=\"$job\"}",
            "format": "table",
            "instant": true,
            "range": false,
            "refId": "A"
          }
        ],
        "title": "Klaytn node status",
        "transformations": [
          {
            "id": "organize",
            "options": {
              "excludeByName": {
                "__name__": true,
                "class": true,
                "job": true
              },
              "indexByName": {
                "Time": 0,
                "Value": 8,
                "__name__": 1,
                "gcmode": 2,
                "instance": 7,
                "job": 3,
                "name": 6,
                "region": 4,
                "service_provider": 5
              },
              "renameByName": {}
            }
          }
        ],
        "type": "table"
      },
      {
        "datasource": {
          "type": "prometheus",
          "uid": "USbDNXl7z"
        },
        "description": "",
        "fieldConfig": {
          "defaults": {
            "color": {
              "mode": "thresholds"
            },
            "custom": {
              "align": "auto",
              "displayMode": "auto",
              "inspect": false
            },
            "mappings": [],
            "thresholds": {
              "mode": "absolute",
              "steps": [
                {
                  "color": "green",
                  "value": null
                },
                {
                  "color": "red",
                  "value": 80
                }
              ]
            }
          },
          "overrides": []
        },
        "gridPos": {
          "h": 9,
          "w": 24,
          "x": 0,
          "y": 11
        },
        "id": 10,
        "options": {
          "footer": {
            "fields": "",
            "reducer": [
              "sum"
            ],
            "show": false
          },
          "showHeader": true
        },
        "pluginVersion": "8.5.2",
        "targets": [
          {
            "datasource": {
              "type": "prometheus",
              "uid": "USbDNXl7z"
            },
            "exemplar": false,
            "expr": "klaytn_blockchain_head_blocknumber{class=\"$class\"}",
            "format": "table",
            "instant": true,
            "interval": "",
            "legendFormat": "",
            "refId": "A"
          }
        ],
        "title": "Klaytn block height",
        "transformations": [
          {
            "id": "organize",
            "options": {
              "excludeByName": {
                "__name__": true,
                "class": true,
                "job": true
              },
              "indexByName": {
                "Time": 0,
                "Value": 8,
                "__name__": 1,
                "gcmode": 2,
                "instance": 7,
                "job": 3,
                "name": 6,
                "region": 5,
                "service_provider": 4
              },
              "renameByName": {}
            }
          }
        ],
        "type": "table"
      },
      {
        "datasource": {
          "type": "prometheus",
          "uid": "USbDNXl7z"
        },
        "description": "",
        "fieldConfig": {
          "defaults": {
            "color": {
              "mode": "thresholds"
            },
            "custom": {
              "align": "auto",
              "displayMode": "auto",
              "inspect": false
            },
            "mappings": [],
            "thresholds": {
              "mode": "absolute",
              "steps": [
                {
                  "color": "green",
                  "value": null
                },
                {
                  "color": "red",
                  "value": 80
                }
              ]
            }
          },
          "overrides": []
        },
        "gridPos": {
          "h": 10,
          "w": 24,
          "x": 0,
          "y": 20
        },
        "id": 12,
        "options": {
          "footer": {
            "fields": "",
            "reducer": [
              "sum"
            ],
            "show": false
          },
          "showHeader": true
        },
        "pluginVersion": "8.5.2",
        "targets": [
          {
            "datasource": {
              "type": "prometheus",
              "uid": "USbDNXl7z"
            },
            "exemplar": false,
            "expr": "process_virtual_memory_bytes{job=\"$job\", class=\"$class\"}/1024/1024/1024",
            "format": "table",
            "instant": true,
            "interval": "",
            "legendFormat": "",
            "refId": "A"
          }
        ],
        "title": "klaytn use memory",
        "transformations": [
          {
            "id": "organize",
            "options": {
              "excludeByName": {
                "class": true,
                "job": true
              },
              "indexByName": {
                "Time": 0,
                "Value": 7,
                "gcmode": 1,
                "instance": 6,
                "job": 3,
                "name": 5,
                "region": 4,
                "service_provider": 2
              },
              "renameByName": {
                "Value": "Value (G)"
              }
            }
          }
        ],
        "type": "table"
      }
    ],
    "refresh": "",
    "schemaVersion": 36,
    "style": "dark",
    "tags": [],
    "templating": {
      "list": [
        {
          "current": {
            "selected": false,
            "text": "klaytn-rpc",
            "value": "klaytn-rpc"
          },
          "datasource": {
            "type": "prometheus",
            "uid": "USbDNXl7z"
          },
          "definition": "label_values(up{class=\"klaytn-rpc-node\"}, job)",
          "hide": 0,
          "includeAll": false,
          "label": "job",
          "multi": false,
          "name": "job",
          "options": [],
          "query": {
            "query": "label_values(up{class=\"klaytn-rpc-node\"}, job)",
            "refId": "StandardVariableQuery"
          },
          "refresh": 1,
          "regex": "",
          "skipUrlSync": false,
          "sort": 1,
          "type": "query"
        },
        {
          "current": {
            "selected": false,
            "text": "klaytn-rpc-node",
            "value": "klaytn-rpc-node"
          },
          "datasource": {
            "type": "prometheus",
            "uid": "USbDNXl7z"
          },
          "definition": "label_values(up{class=\"klaytn-rpc-node\"}, class)",
          "hide": 0,
          "includeAll": false,
          "label": "Class",
          "multi": false,
          "name": "class",
          "options": [],
          "query": {
            "query": "label_values(up{class=\"klaytn-rpc-node\"}, class)",
            "refId": "StandardVariableQuery"
          },
          "refresh": 1,
          "regex": "",
          "skipUrlSync": false,
          "sort": 0,
          "type": "query"
        }
      ]
    },
    "time": {
      "from": "now-6h",
      "to": "now"
    },
    "timepicker": {},
    "timezone": "",
    "title": "klaytn",
    "uid": "Mm8-x0Pnk",
    "version": 10,
    "weekStart": ""
  }
