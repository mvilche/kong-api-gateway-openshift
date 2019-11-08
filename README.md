# Kong Api Gateway + Konga Dashboard Administrator

# Features

- Non-root
- Openshift compatible
- S2i build images

### Environments

| Environment | Details |
| ------ | ------ |
| TIMEZONE | Set Timezone (America/Montevideo, America/El_salvador) |
| WAITFOR_HOST | set name host |
| WAITFOR_PORT | set port for WAITFOR_HOST |


### Deploy

```console

 oc create -f kong-template-openshift.yaml -n kong-api-gateway

```

License
----

Martin vilche
