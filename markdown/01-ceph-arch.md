# Ceph Architektur


<!-- .slide: data-background-image="images/ceph_architektur.svg" data-background-size="contain" data-background-size="1024px" -->


### Ceph-Monitor
![img](images/ceph_architektur_ceph-mon.png) <!-- .element: height="200px" border="none" -->

Codename: `ceph-mon`

* Verwaltung der MAPS
* Quorum / PAXOS


### Ceph Object Storage Daemon
![img](images/ceph_architektur_ceph-osd.png) <!-- .element: height="200px" -->

Codename: `ceph-osd`

* speichert Daten
* pro Drive ein Prozess
* SPoF


### Ceph Metadata Server
![img](images/ceph_architektur_ceph-mds.png) <!-- .element: height="200px" -->

Codename: `ceph-mds`

* zuständig für Filesystem(e)
* Active/Passive**


### Ceph Manager
![img](images/ceph_architektur_ceph-mgr.png) <!-- .element: height="200px" -->

Codename: `ceph-mgr`

* ab 12.x.x 'Pflicht'
* Active/Passive


### Ceph RadosGW
![img](images/ceph_architektur_radosgw.png) <!-- .element: height="200px" -->

Codename: `radosgw`

* S3-kompatible API
* Active/Passive


# CRUSH

*C*ontrolled *R*eplication *U*nder *S*calable *H*ashing


* `a scalable pseudo random data distribution function`
* Wie?
  * via `crush rules`
* Wo?
  * via `device-class`
  * Location / Pools

```
hash(object_name) ⇨ PG ID
crush(pg id, topology) ⇨ ["osd.23", "osd.42", "osd.1337"]
```


![img](https://github.com/rrmichel/ceph-cheatsheet/raw/master/images/ceph-pg-osd-mapping.png)<!-- .element: height="600px" -->


# RADOS

*R*eliable *A*utonomic *D*istributed *O*bject *S*tore

* Kernkomponente
* Implementiert
  * Self-Healing
  * Self-Management
