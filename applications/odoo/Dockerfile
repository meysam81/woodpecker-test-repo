ARG ODOO_VERSION=19.0
FROM odoo:${ODOO_VERSION}

USER root

COPY requirements.txt /tmp/requirements.txt
RUN pip install --no-cache-dir -r /tmp/requirements.txt

COPY enterprise /opt/odoo/enterprise

ENV ODOO_ADDONS_PATH="/opt/odoo/enterprise,/usr/lib/python3/dist-packages/odoo/addons"

USER odoo

HEALTHCHECK --interval=30s --timeout=10s --start-period=60s --retries=3 \
    CMD curl -f http://127.0.0.1:8069/web/health || exit 1
