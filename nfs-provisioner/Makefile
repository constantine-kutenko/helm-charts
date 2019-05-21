
CHART_NAME="nfs-provisioner"
RELEASE_NAME="nfs-provisioner"
NAMESPACE="kube-system"
ENV="production"

lint:
		@clear
		@/usr/local/bin/helm lint --strict ${CHART_NAME}


template:
		@clear
		@/usr/local/bin/helm template ${CHART_NAME}


install:
		@clear
		@/usr/local/bin/helm del --purge nfs-provisioner; exit 0
		@/usr/local/bin/helm install \
			--name ${RELEASE_NAME} \
			--namespace ${NAMESPACE} \
			--set environment=${ENV} \
			${CHART_NAME}
		@/usr/local/bin/helm list | grep ${RELEASE_NAME}

upgrade:
		@clear
		@/usr/local/bin/helm get values --all ${RELEASE_NAME} > /tmp/${RELEASE_NAME}.values
		@/usr/local/bin/helm upgrade \
			-f /tmp/${RELEASE_NAME}.values \
			--set environment=${ENV} \
			${RELEASE_NAME} \
			./${CHART_NAME}
		@rm -f /tmp/${RELEASE_NAME}.values
		@/usr/local/bin/helm list | grep ${RELEASE_NAME}
