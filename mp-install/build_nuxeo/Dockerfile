FROM nuxeo:10.10
# This Dockerfile installs Nuxeo hotfixes up to a specific version.

# A CLID is required in order to install hotfixes
# Make sure to set correct permissions on instance.clid; if they are wrong
# nuxeoctl won't be able to access it
COPY --chown=nuxeo:0 instance.clid /var/lib/nuxeo/data/instance.clid
# Bake hotfixes into the image
RUN /docker-entrypoint.sh nuxeoctl mp-install --accept=true nuxeo-10.10-HF28

# Cleanup
USER root
RUN for i in "/var/lib/nuxeo/data" "/var/log/nuxeo"; do \
      mkdir -p $i && chown -fR nuxeo:0 $i && chmod -fR g+rwX $i; \
    done && \
    chown -f nuxeo:0 /etc/nuxeo/nuxeo.conf && chmod -f g+rw /etc/nuxeo/nuxeo.conf && \
    chmod 770 /var/log/nuxeo
# Remove the CLID from the build as we should use the "correct" one at runtime
# Clear the "configured" flag so that the container will correctly handle any
# params at runtime
RUN rm /var/lib/nuxeo/data/instance.clid && rm ${NUXEO_HOME}/configured

USER 1000