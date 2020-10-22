# issan-organizaciones
Cambie lo siguiente:
* Sacque la variable del standalone.xml y la meti al moenmnto de crear la aplicacion en openshift.
* Para poder acceder con diferentes host cambien en el standalone xml el inet (jboss.bind.address.management=0.0.0.0 ??? -Djboss.bind.address=0.0.0.0 ???)

1 - crear la aplicacion
C:>oc new-app --name bps https://github.com/bfagalde/issan-organizaciones#prueba1_env --context-dir dockerfiles -e COUNTRY_MEMBER_PATH=/opt/eap/standalone/configuration/URUGUAY
C:>oc new-app --name bps https://github.com/bfagalde/issan-organizaciones#prueba1_env --context-dir dockerfiles -e COUNTRY_MEMBER_PATH=/opt/eap/standalone/configuration/URUGUAY -e COUNTRY=URUGUAY -e JBOSS_HOME=/opt/eap/

2 - crear la ruta "oc expose svc/bps"

2 - modificar la ruta para hacera ssl.

por ultimo...
https://bps-bfagalde-uy.bps-1580412573509-f72ef11f3ab089a8c677044eb28292cd-0001.eu-de.containers.appdomain.cloud/upload-site/

-----------------
C:\data\git\bps\git-hub\issan-organizaciones\dockerfiles>oc logs -f bc/uy-bps-client
Cloning "https://github.com/bfagalde/issan-organizaciones" ...
        Commit: beecf6348c2ca70d53244a756a62bea5c673f9f6 (habilitando multiples host)
        Author: Bernardo Fagalde <bfagalde@bps.gub.uy>
        Date:   Sun Oct 18 22:32:32 2020 -0300
Replaced Dockerfile FROM image registry.access.redhat.com/jboss-eap-7/eap72-openshift
Step 1/11 : FROM registry.access.redhat.com/jboss-eap-7/eap72-openshift@sha256:464e00edbf44d91820b9d9e95edbe6c68e075b85158f60e3d2298d94c9ec56b0
 ---> e3a06e233f32
Step 2/11 : COPY config/jboss/modules/org $JBOSS_HOME/modules/org
 ---> b62f3f70bb6e
Removing intermediate container 081481fe581e
Step 3/11 : COPY config/jboss/modules/uy $JBOSS_HOME/modules/uy
 ---> 8c66e4bc1235
Removing intermediate container c2964abc7711
Step 4/11 : COPY Luis_Galusso_0x927412E2_public.asc $JBOSS_HOME/standalone/configuration
 ---> 39bd1276caa4
Removing intermediate container 0c57032bb713
Step 5/11 : COPY Luis_Galusso_0x927412E2_SECRET.asc $JBOSS_HOME/standalone/configuration
 ---> 8ac739f1890c
Removing intermediate container 0e7852c8fdb1
Step 6/11 : COPY standalone.xml $JBOSS_HOME/standalone/configuration/standalone-openshift.xml
 ---> dc5db7286a99
Removing intermediate container 865f4ea32352
Step 7/11 : COPY config/issan-gateway/ESPANA $JBOSS_HOME/standalone/configuration/ESPANA
 ---> 374122a97ee1
Removing intermediate container b5d299b4d33a
Step 8/11 : COPY config/issan-gateway/URUGUAY $JBOSS_HOME/standalone/configuration/URUGUAY
 ---> ee57e7136a36
Removing intermediate container f77a8112de54
Step 9/11 : COPY upload-site.war $JBOSS_HOME/standalone/deployments/
 ---> 227de8e3c887
Removing intermediate container ed10d0a0dda8
Step 10/11 : ENV "OPENSHIFT_BUILD_NAME" "uy-bps-client-1" "OPENSHIFT_BUILD_NAMESPACE" "issan-orgs" "OPENSHIFT_BUILD_SOURCE" "https://github.com/bfagalde/issan-organizaciones" "OPENSHIFT_BUILD_REFERENCE" "prueba1_env" "OPENSHIFT_BUILD_COMMIT" "beecf6348c2ca70d53244a756a62bea5c673f9f6"
 ---> Running in 712b4c34ff87
 ---> fef67d700f26
Removing intermediate container 712b4c34ff87
Step 11/11 : LABEL "io.openshift.build.commit.author" "Bernardo Fagalde \u003cbfagalde@bps.gub.uy\u003e" "io.openshift.build.commit.date" "Sun Oct 18 22:32:32 2020 -0300" "io.openshift.build.commit.id" "beecf6348c2ca70d53244a756a62bea5c673f9f6" "io.openshift.build.commit.message" "habilitando multiples host" "io.openshift.build.commit.ref" "prueba1_env" "io.openshift.build.name" "uy-bps-client-1" "io.openshift.build.namespace" "issan-orgs" "io.openshift.build.source-context-dir" "dockerfiles" "io.openshift.build.source-location" "https://github.com/bfagalde/issan-organizaciones"
 ---> Running in e89377ce1329
 ---> 3aae1246a374
Removing intermediate container e89377ce1329
Successfully built 3aae1246a374

Pushing image docker-registry.default.svc:5000/issan-orgs/uy-bps-client:latest ...
Pushed 0/11 layers, 18% complete
Pushed 1/11 layers, 45% complete
Pushed 2/11 layers, 45% complete
Pushed 3/11 layers, 45% complete
Pushed 4/11 layers, 45% complete
Pushed 5/11 layers, 46% complete
Pushed 6/11 layers, 73% complete
Pushed 7/11 layers, 73% complete
Pushed 8/11 layers, 73% complete
Push successful
