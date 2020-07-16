FROM nuxeo:10.10
COPY --chown=nuxeo:0 instance.clid /var/lib/nuxeo/data/instance.clid
RUN /docker-entrypoint.sh nuxeoctl mp-hotfix --accept=true
# Cleanup
USER root
RUN for i in "/var/lib/nuxeo/data" "/var/log/nuxeo"; do \
      mkdir -p $i && chown -fR nuxeo:0 $i && chmod -fR g+rwX $i; \
    done && \
    chown -f nuxeo:0 /etc/nuxeo/nuxeo.conf && chmod -f g+rw /etc/nuxeo/nuxeo.conf && \
    chmod 770 /var/log/nuxeo
RUN rm /var/lib/nuxeo/data/instance.clid && rm ${NUXEO_HOME}/configured
USER 1000
