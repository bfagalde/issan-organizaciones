#FROM nexus.bps.net:5000/redhat.io/jboss-eap-7/eap72-openshift:latest
FROM registry.access.redhat.com/jboss-eap-7/eap72-openshift

COPY config/jboss/modules/org $JBOSS_HOME/modules/org
COPY config/jboss/modules/uy $JBOSS_HOME/modules/uy

# Copiamos las llaves publicas y privadas para el encriptado y firma
COPY Luis_Galusso_0x927412E2_public.asc $JBOSS_HOME/standalone/configuration
COPY Luis_Galusso_0x927412E2_SECRET.asc $JBOSS_HOME/standalone/configuration

# definir variable de entorno COUNTRY con valor URUGUAY o ESPAÑA
COPY standalone.xml $JBOSS_HOME/standalone/configuration/standalone-openshift.xml

COPY config/issan-gateway/ESPANA $JBOSS_HOME/standalone/configuration/ESPANA
COPY config/issan-gateway/URUGUAY $JBOSS_HOME/standalone/configuration/URUGUAY

# add deployment files
COPY upload-site.war $JBOSS_HOME/standalone/deployments/