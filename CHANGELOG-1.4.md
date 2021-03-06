  * [v1.4.0](#v140)
     * [Downloads for v1.4.0](#downloads-for-v140)
        * [KubeEdge Binaries](#kubeedge-binaries)
        * [Installer Binaries](#installer-binaries)
        * [EdgeSite Binaries](#edgesite-binaries)
     * [KubeEdge v1.4 Release Notes](#kubeedge-v14-release-notes)
        * [1.4 What's New](#14-whats-new)
        * [Important Steps before Upgrading](#important-steps-before-upgrading)       
        * [Other Notable Changes](#other-notable-changes)
        * [Bug Fixes](#bug-fixes)
  * [v1.4.0-beta.0](#v140-beta0)
     * [Changelog since v1.3.1](#changelog-since-v131)
        * [Bug Fixes](#bug-fixes-1)
        
# v1.4.0

## Downloads for v1.4.0

### KubeEdge Binaries
| filename | Size | sha512 hash |
| -------- | ---- | ----------- |


### Installer Binaries
| filename | Size | sha512 hash |
| -------- | ---- | ----------- |

### EdgeSite Binaries
| filename | Size | sha512 hash |
| -------- | ---- | ----------- |

## KubeEdge v1.4 Release Notes

### 1.4 What's New

**Enhance Devices Management**

Upgrade device API from v1alpha1 to v1alpha2, enhancement include: 

- A new field is added to explicitly provide customized protocol support
- Introduced `data` section to allow users defining data to get and process on the edge
- Moved `propertyVistors` from device model to Device instance API

Users are now able to customize the protocol of the edge device and also able to get and process the date in edge side.([#1687](https://github.com/kubeedge/kubeedge/pull/1687), [@luogangyi](https://github.com/luogangyi), [@kevin-wangzefeng](https://github.com/kevin-wangzefeng)).

**Metrics-Server Support for metrics collection across cloud and edge**

Users are now able to deploy metrics-server to collect resource metrics from edge nodes. Follow the [instructions here](/docs/setup/keadm.md#support-metrics-server-in-cloud) to deploy the metrics-server. ([#1735](https://github.com/kubeedge/kubeedge/pull/1735), [@Poor12](https://github.com/Poor12), [@kadisi](https://github.com/kadisi)).

**EdgeNode Certificate Rotation**

EdgeNodes are now able to automatically apply for new certificate when the certificate is about to expire and enforce TLS between CloudCore and EdgeCore. ([#1838](https://github.com/kubeedge/kubeedge/pull/1838), [@XJangel](https://github.com/XJangel), [@fisherxu](https://github.com/fisherxu))

**Kubernetes Dependencies Upgrade**

Upgrade the venderod kubernetes version to v1.18.6, users now can use the feature of new version
on the cloud and on the edge side. ([#1982](https://github.com/kubeedge/kubeedge/pull/1982), [@dingyin](https://github.com/dingyin))

### Important Steps before Upgrading

**Device CRD API change**

KubeEdge Device Controller now only reflects v1alpha2 for Device CRD, please make sure [Device v1alpha2](https://github.com/kubeedge/kubeedge/blob/release-1.4/build/crds/devices/devices_v1alpha2_device.yaml) and [DeviceModel v1alpha2](https://github.com/kubeedge/kubeedge/blob/release-1.4/build/crds/devices/devices_v1alpha2_devicemodel.yaml) installed, and you would need to manually convert their existing custom resources from v1alpha1 to v1alpha2.

It's recommended to keep v1alpha1 CRD and custom resources in the cluster or exported somewhere before upgrading, in case any rollback is needed.

### Other Notable Changes

- update golang to 1.14 ([#1539](https://github.com/kubeedge/kubeedge/pull/1539), [@subpathdev](https://github.com/subpathdev))
- Support metrics-server in cloud ([#1735](https://github.com/kubeedge/kubeedge/pull/1735), [@Poor12](https://github.com/Poor12))
- Keadm: support raspbian ([#1779](https://github.com/kubeedge/kubeedge/pull/1779), [@daixiang0](https://github.com/daixiang0))
- Implement device management enhance ([#1790](https://github.com/kubeedge/kubeedge/pull/1790), [@luogangyi](https://github.com/luogangyi))
- Support edge certificate rotation  ([#1838](https://github.com/kubeedge/kubeedge/pull/1838), [@XJangel](https://github.com/XJangel))
- Add tree to store copy of dependency's license ([#1847](https://github.com/kubeedge/kubeedge/pull/1847), [@kevin-wangzefeng](https://github.com/kevin-wangzefeng))
- add garbage collection of reliablesyncs when node unregisters ([#1855](https://github.com/kubeedge/kubeedge/pull/1855), [@ls889](https://github.com/ls889))
- fix too long time to get node ready when reconnect  ([#1670](https://github.com/kubeedge/kubeedge/pull/1670), [@fisherxu](https://github.com/fisherxu))
- fix cpu limit does not take effect issue ([#1866](https://github.com/kubeedge/kubeedge/pull/1866), [@Baoqiang-Zhang](https://github.com/Baoqiang-Zhang))
- Auto detect sandbox image ([#1866](https://github.com/kubeedge/kubeedge/pull/1874), [@daixiang0](https://github.com/daixiang0))
- Run edgecore as system service ([#1962](https://github.com/kubeedge/kubeedge/pull/1962), [@dingyin](https://github.com/dingyin))
- Update vendor to Kubernetes 1.18 ([#1982](https://github.com/kubeedge/kubeedge/pull/1982), [@dingyin](https://github.com/dingyin))
- extend property types ([#2014](https://github.com/kubeedge/kubeedge/pull/2014), [@luogangyi](https://github.com/luogangyi))

### Bug Fixes

- fix wrong use of e.namespace when get imagePullSecret ([#1765](https://github.com/kubeedge/kubeedge/pull/1765), [@GsssC](https://github.com/GsssC))
- fix wrong parse operation when service url is short ([#1775](https://github.com/kubeedge/kubeedge/pull/1775), [@XiaoJiangWang](https://github.com/XiaoJiangWang))
- delay the volume mount until the pods are retrieved from metaManger and added to managers when edgecore starts ([#1809](https://github.com/kubeedge/kubeedge/pull/1809), [@GsssC](https://github.com/GsssC))
- edged.go: Fix pod sync copied from kubelet ([#1819](https://github.com/kubeedge/kubeedge/pull/1819), [@faicker](https://github.com/faicker))
- Improve metrics connection ([#1887](https://github.com/kubeedge/kubeedge/pull/1887), [@Poor12](https://github.com/Poor12))
- fix use certificate from local directory problem ([#1925](https://github.com/kubeedge/kubeedge/pull/1925), [@threestoneliu](https://github.com/threestoneliu))
- Process of bluetooth mapper scheduler seems wrong ([#1940](https://github.com/kubeedge/kubeedge/pull/1940), [@sailorvii](https://github.com/sailorvii))
- Fix device configMap can not be re-created ([#1949](https://github.com/kubeedge/kubeedge/pull/1949), [@daixiang0](https://github.com/daixiang0))
- fixed goroutine leak, when ws connection reconnect, but fifo's channel no close ([#2019](https://github.com/kubeedge/kubeedge/pull/2019), [@loongify](https://github.com/loongify))
- panic when multiple goroutine concurrency access same map ([#2037](https://github.com/kubeedge/kubeedge/pull/2037), [@Yellow-L](https://github.com/Yellow-L))

# v1.4.0-beta.0

## Changelog since v1.3.1

- Keadm: support raspbian (https://github.com/kubeedge/kubeedge/pull/1779, @daixiang0)
- Implement device management enhance (https://github.com/kubeedge/kubeedge/pull/1790, @luogangyi)
- Support edge certificate rotation  (https://github.com/kubeedge/kubeedge/pull/1838, @XJangel)
- Add tree to store copy of dependency's license (https://github.com/kubeedge/kubeedge/pull/1847, @kevin-wangzefeng)
- add garbage collection of reliablesyncs when node unregisters (https://github.com/kubeedge/kubeedge/pull/1855, @ls889)
- fix too long time to get node ready when reconnect  (https://github.com/kubeedge/kubeedge/pull/1670, @fisherxu)
- fix cpu limit does not take effect issue (https://github.com/kubeedge/kubeedge/pull/1866, @Baoqiang-Zhang)
- Auto detect sandbox image (https://github.com/kubeedge/kubeedge/pull/1874, @daixiang0 )
- Run edgecore as system service (https://github.com/kubeedge/kubeedge/pull/1962, @dingyin)
- Update vendor to Kubernetes 1.18 (https://github.com/kubeedge/kubeedge/pull/1982, @dingyin)
- extend property types (https://github.com/kubeedge/kubeedge/pull/2014, @luogangyi)

### Bug Fixes

- fix wrong use of e.namespace when get imagePullSecret (https://github.com/kubeedge/kubeedge/pull/1765, @GsssC)
- fix wrong parse operation when service url is short (https://github.com/kubeedge/kubeedge/pull/1775, @XiaoJiangWang)
- delay the volume mount until the pods are retrieved from metaManger and added to managers when edgecore starts (https://github.com/kubeedge/kubeedge/pull/1809, @GsssC)
- edged.go: Fix pod sync copied from kubelet (https://github.com/kubeedge/kubeedge/pull/1819, @faicker)
- Improve metrics connection (https://github.com/kubeedge/kubeedge/pull/1887, @Poor12)
- fix use certificate from local directory problem (https://github.com/kubeedge/kubeedge/pull/1925, @threestoneliu)
- Process of bluetooth mapper scheduler seems wrong (https://github.com/kubeedge/kubeedge/pull/1940, @sailorvii)
- Fix device configMap can not be re-created (https://github.com/kubeedge/kubeedge/pull/1949, @daixiang0)
- fixed goroutine leak, when ws connection reconnect, but fifo's channel no close (https://github.com/kubeedge/kubeedge/pull/2019, @loongify)
