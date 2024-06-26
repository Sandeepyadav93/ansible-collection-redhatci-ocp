# End to End Tests Suites Role

[OpenShift End to End tests](https://github.com/openshift/openshift-tests) are available as a container image in registry.redhat.io/openshift4/ose-tests.

The tests supported by this role are:
 - [OpenShift conformance tests](https://github.com/openshift/openshift-tests)
 - [CSI driver tests](https://redhat-connect.gitbook.io/openshift-badges/badges/container-storage-interface-csi-1/workflow/test-environment) (Badge)

## Variables

The tests executed are defined by the the variable values provided to the role.

Name                               | Default                                    | Description
---------------------------------- | ------------------------------------------ | -------------------------------------------------------------
ts\_e2e\_image                     | quay.io/openshift/origin-tests"            | Image used to execute the tests
ts\_registry                       | registry.dfwt5g.lab:4443                   | Registry used to pull/push images the required images
ts\_registry\_auth                 | auths.json                                 | File with pull secrets for the registries
ts\_ocp\_version\_maj              | 4                                          | OCP version major number, it is recommended to match with the target cluster version
ts\_ocp\_version\_min              | 7                                          | OCP version minor number, it is recommended to match with the target cluster version
ts\_registry\_certificate          | domain.crt                                 | TLS certificate for the registry, if required
ts\_conformance\_tests             | ''                                         | Conformance test to execute
ts\_configs\_dir                   | /home/user/clusterconfigs/                 | Directory that hosts the kubeconfig files and other cluster files that may need to be passed mounted in the test container. This directory will be also used to store the test results.
ts\_csi\_tests\_dir                | /home/user/clusterconfigs/                 | Directory that hosts additional files required during the testing
ts\_csi\_test\_manifest            | ''                                         | Test manifest to be used for the CSI driver tests
ts_log_dir                         | /tmp                                       | Directory where the logs and results will be stored. If provided, the CSI tests will be provided as described in the OpenShift Badges documentation](https://redhat-connect.gitbook.io/openshift-badges/badges/container-network-interface-csi)
ts_do_cni_tests                    | false                                      | Executes the CNI tests as described in the [OpenShift Badges documentation](https://redhat-connect.gitbook.io/openshift-badges/badges/container-network-interface-cni)
ts_do_virt_tests                   | false                                      | Execute the KubeVirt Conformance tests as described in the [OpenShift Badges documentation](https://redhat-connect.gitbook.io/openshift-badges/badges/container-network-interface-cnii). Hyperconverged operator must be installed on the cluster. For air-gapped environments this is only supported on OCP 4.9 and newer versions.
ts_sonobuoy_version                | v0.56.4                                    | [Sonobuoy](https://sonobuoy.io/) version to be used for the tests
ts_kubevirt_conformance_version:   | v0.52.0                                    | [KubeVirt](https://github.com/kubevirt/kubevirt/releases/) conformance release to be used for the tests
