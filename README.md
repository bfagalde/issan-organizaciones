# issan-organizaciones
Cambie lo siguiente:
* Sacque la variable del standalone.xml y la meti al moenmnto de crear la aplicacion en openshift.
* Para poder acceder con diferentes host cambien en el standalone xml el inet (jboss.bind.address.management=0.0.0.0 ??? -Djboss.bind.address=0.0.0.0 ???)

C:\>oc new-app --name uy-bps-client https://github.com/bfagalde/issan-organizaciones#prueba1_env --context-dir dockerfiles
