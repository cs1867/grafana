# Makefile for perfSONAR Grafana
#
default:
	@true

install:
ifndef PERFSONAR-ROOTPATH
	@echo No PERFSONAR-ROOTPATH specified for installation
	@false
endif
ifndef HTTPD-CONFIGPATH
	@echo No HTTPD-CONFIGPATH specified for installation
	@false
endif
	mkdir -p ${PERFSONAR-ROOTPATH}
	mkdir -p ${HTTPD-CONFIGPATH}
	mkdir -p ${PERFSONAR-ROOTPATH}/images
	mkdir -p ${PERFSONAR-ROOTPATH}/plugins
	mkdir -p ${PERFSONAR-ROOTPATH}/provisioning
	mkdir -p ${PERFSONAR-ROOTPATH}/provisioning/dashboards
	mkdir -p ${PERFSONAR-ROOTPATH}/provisioning/datasources
	install -m 755 grafana_common.sh ${PERFSONAR-ROOTPATH}/
	install -m 755 grafana_config.sh ${PERFSONAR-ROOTPATH}/
	install -m 755 grafana_plugin_download.sh ${PERFSONAR-ROOTPATH}/
	install -m 755 grafana_config.py ${PERFSONAR-ROOTPATH}/
	install -m 755 grafana_folder_permissions.py ${PERFSONAR-ROOTPATH}/
	install -m 644 apache-grafana.conf ${HTTPD-CONFIGPATH}/
	install -m 644 images/* ${PERFSONAR-ROOTPATH}/images
	install -m 644 provisioning/dashboards/* ${PERFSONAR-ROOTPATH}/provisioning/dashboards
	install -m 644 provisioning/datasources/* ${PERFSONAR-ROOTPATH}/provisioning/datasources
	${PERFSONAR-ROOTPATH}/grafana_plugin_download.sh ${PERFSONAR-ROOTPATH}/plugins
	cp -r dashboards/ ${PERFSONAR-ROOTPATH}/dashboards