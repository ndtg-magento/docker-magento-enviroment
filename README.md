![Docker Stars](https://img.shields.io/docker/stars/ntuangiang/magento-system.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/ntuangiang/magento-system.svg)
![Docker Automated build](https://img.shields.io/docker/automated/ntuangiang/magento-system.svg)

# Magento 2.4.3-p1 Docker

[https://devdocs.magento.com](https://devdocs.magento.com) Meet the small business, mid-sized business, and enterprise-level companies who are benefiting from the power and flexibility of Magento on their web stores. We built the eCommerce platform, so you can build your business.

## Docker Repository
[ntuangiang/magento-system](https://hub.docker.com/r/ntuangiang/magento-system) 

## Usage
### Developer
- Write a `Dockerfile` file.

```Dockerfile
FROM ntuangiang/magento-system:2.4.3-p1 as magento-phpfpm
# magento-builder is a image from ntuangiang/magento-cache-system:2.4.3-p1

COPY --from=magento-builder --chown=magento:magento \
    "${ZIP_ROOT}/magento.zip" \
    ${ZIP_ROOT}/

# If we zip a folder, unzip will auto exact folder we zipped.
RUN unzip -qq "${ZIP_ROOT}/magento.zip" -d "/"

USER root

RUN rm -rf "${ZIP_ROOT}/magento.zip"

USER magento
```

## LICENSE

MIT License
