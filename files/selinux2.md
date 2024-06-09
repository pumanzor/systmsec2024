SELinux fue desarrollado como una solución adicional de seguridad para Linux que utiliza el marco de seguridad en el núcleo de Linux. El propósito era permitir una política de seguridad más granular 
que vaya más allá de lo que ofrecen los permisos predeterminados de Lectura, Escritura y Ejecución, y más allá de asignar permisos a las diferentes capacidades disponibles en Linux. 
SELinux hace esto interceptando todas las llamadas al sistema que llegan al núcleo y negándolas por defecto. Esto significa que en un sistema con SELinux habilitado y sin ninguna otra configuración, 
nada funcionará. Para permitir que tu sistema haga cualquier cosa, como administrador tendrás que escribir reglas y colocarlas en una política.

Un ejemplo explica por qué se necesita una solución como SELinux (o su contraparte AppArmor):

"Una mañana, descubrí que mi servidor había sido hackeado. El servidor estaba ejecutando una instalación de SLES completamente parcheada. Tenía un firewall configurado y no ofrecía servicios innecesarios. 
Un análisis más detallado reveló que el hacker había entrado a través de un script PHP vulnerable que formaba parte de uno de los hosts virtuales de Apache que estaban ejecutándose en este servidor. 
El intruso había logrado acceder a un shell usando la cuenta wwwrun que utilizaba el servidor web Apache. Como este usuario wwwrun, el intruso había creado varios scripts en los directorios /var/tmp 
y /tmp, que formaban parte de una botnet que estaba lanzando un ataque de Denegación de Servicio Distribuido contra varios servidores."

Lo interesante de este hackeo es que ocurrió en un servidor donde realmente no había nada mal. Todos los permisos estaban configurados correctamente, pero el intruso logró entrar en el sistema. 
Lo que queda claramente evidente en este ejemplo es que en algunos casos se necesita seguridad adicional, una seguridad que va más allá de lo que ofrece SELinux. Como una alternativa menos completa 
y menos compleja, se puede usar AppArmor.

AppArmor limita las capacidades específicas de los procesos para leer/escribir y ejecutar archivos (y otras cosas). Su enfoque es principalmente que las cosas que ocurren dentro de un proceso no pueden escapar.

En cambio, SELinux utiliza etiquetas adjuntas a objetos (por ejemplo, archivos, binarios, sockets de red) y las utiliza para determinar los límites de privilegios, construyendo así un nivel de confinamiento 
que puede abarcar más que un proceso o incluso todo el sistema.

SELinux fue desarrollado por la Agencia de Seguridad Nacional de los Estados Unidos (NSA), y desde el principio, Red Hat ha estado fuertemente involucrado en su desarrollo. La primera versión de SELinux se 
ofreció en la era de Red Hat Enterprise Linux 4™, alrededor del año 2006. Al principio solo ofrecía soporte para servicios esenciales, pero con los años se ha desarrollado en un sistema que ofrece muchas 
reglas que se recopilan en políticas para ofrecer protección a una amplia gama de servicios.

SELinux se desarrolló de acuerdo con algunos estándares de certificación como Common Criteria y FIPS 140. Debido a que algunos clientes solicitaron específicamente soluciones que cumplían con estos 
estándares, SELinux se volvió rápidamente relativamente popular.

Como una alternativa a SELinux, Immunix, una empresa que fue comprada por Novell en 2005, había desarrollado AppArmor. AppArmor se construyó sobre los mismos principios de seguridad que SELinux, pero 
adoptó un enfoque completamente diferente, donde era posible restringir los servicios exactamente a lo que necesitaban hacer mediante un procedimiento guiado fácil de usar. Sin embargo, AppArmor nunca 
ha alcanzado el mismo estatus que SELinux, incluso si hay algunos buenos argumentos para asegurar un servidor con AppArmor en lugar de con SELinux.

Debido a que muchas organizaciones están solicitando que SELinux esté en las distribuciones de Linux que están utilizando, SUSE ofrece soporte para el marco de SELinux en SUSE Linux Enterprise Server. 
Esto no significa que la instalación predeterminada de SUSE Linux Enterprise Server cambiará de AppArmor a SELinux en un futuro cercano.