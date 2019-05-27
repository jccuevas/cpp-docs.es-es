---
title: 'vcpkg: un administrador de paquetes de C++ para Windows, Linux y MacOS'
description: Vcpkg es un administrador de paquetes de la línea de comandos que simplifica en gran medida la adquisición e instalación de bibliotecas de C++ de código abierto en Windows.
author: mikeblome
ms.author: mblome
ms.date: 05/16/2019
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 58f8a9b8223dc54bf083ebbac97528f88890777c
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837022"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: un administrador de paquetes de C++ para Windows, Linux y MacOS

vcpkg es un administrador de paquetes de línea de comandos que simplifica considerablemente la adquisición e instalación de bibliotecas de terceros en Windows, Linux y MacOS. Si se usan bibliotecas de terceros en el proyecto, conviene usar vcpkg para instalarlas. Vcpkg admite bibliotecas tanto de código abierto como propietarias. Se ha probado la compatibilidad de todas las bibliotecas del catálogo de Windows vcpkg con Visual Studio 2015, Visual Studio 2017 y Visual Studio 2019. A partir de mayo de 2018, hay más de 900 bibliotecas en el catálogo de Windows y más de 350 en el de Linux/MacOS. La comunidad de C++ agrega más bibliotecas a los catálogos de forma continuada.

## <a name="simple-yet-flexible"></a>Simple, pero flexible

Con un solo comando se pueden descargar orígenes y compilar una biblioteca. Vcpkg es, en sí mismo, un proyecto de código abierto disponible en GitHub. Puede personalizar sus clones privados del modo que quiera. Por ejemplo, puede especificar diferentes bibliotecas o distintas versiones de las bibliotecas que figuran en el catálogo público. Puede tener varios clones de vcpkg en un mismo equipo y que cada uno de ellos genere conjuntos personalizados de bibliotecas o conmutadores de compilación, etc. Cada clon es un entorno autónomo y, como tal, posee su propia copia de vcpkg.exe que solo funciona en su jerarquía. Vcpkg no se agrega a ninguna variable de entorno y no tiene ninguna dependencia en el Registro de Windows ni en Visual Studio.

## <a name="sources-not-binaries"></a>Orígenes no binarios

Para las bibliotecas del catálogo de Windows, vcpkg descarga orígenes en lugar de archivos binarios[1]. Compila esos orígenes con la versión más reciente de Visual Studio que puede encontrar. En C++, es muy importante las bibliotecas que se usen se hayan compilado con el mismo compilador y la misma versión de compilador que el código de la aplicación que vincula. Al usar vcpkg, se elimina (o al menos se reduce notablemente) la posibilidad de que haya una discrepancia en los binarios y los problemas que pueden derivarse de ello. En los equipos que están estandarizados en una versión específica de un compilador, un miembro del equipo puede usar vcpkg para descargar los orígenes y compilar un conjunto de archivos binarios y, después, usar el comando de exportación para comprimir los archivos binarios y los encabezados para otros miembros del equipo. Para obtener más información, vea [Exportación de archivos binarios y encabezados compilados](#export_binaries_per_project) a continuación.

Si crea un clon de vcpkg con bibliotecas privadas en la colección de puertos, puede agregar un puerto que descargue encabezados y archivos binarios ya creados previamente y escribir un archivo portfile.cmake que, simplemente, copie tales archivos en la ubicación que quiera.

[1] *Nota: En el caso de algunas bibliotecas propietarias, no hay ningún origen disponible. En tal caso, vcpkg descargará archivos binarios creados previamente compatibles.*

## <a name="installation"></a>Instalación

Clone el repositorio vcpkg de GitHub: [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg). Puede descargarlo en la ubicación de carpeta que prefiera.

Ejecute el programa previo en la carpeta raíz:

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux, MacOS)

## <a name="search-the-list-of-available-libraries"></a>Búsqueda en la lista de bibliotecas disponibles

Para ver los paquetes disponibles, escriba **vcpkg search** en el símbolo del sistema.

Con este comando se enumeran los archivos de control contenidos en las subcarpetas vcpkg/ports. La lista será similar a la siguiente:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Puede filtrar por patrón, por ejemplo, **vcpkg search ta**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Instalación de una biblioteca en el equipo local

Tras obtener el nombre de una biblioteca por medio de **vcpkg search**, hay que usar **vcpkg install** para descargar la biblioteca y compilarla. Vcpkg usa el archivo portfile de la biblioteca en el directorio ports. Si no se especifica ningún triplo, vcpkg instalará y compilará para el predeterminado de la plataforma de destino: x86-windows, x64-linux.cmake o x64-osx.cmake.

Para las bibliotecas de Linux, vcpkg depende de que gcc esté instalado en el equipo local. En MacOS, vcpkg usa Clang.

Si en el archivo portfile hay especificada alguna dependencia, vcpkg también la descargará e instalará. Tras la descarga, vcpkg compila la biblioteca usando el sistema de compilación que la biblioteca use. Se prefieren los proyectos de CMake y MSBuild (en Windows), pero se admite MAKE junto con cualquier otro sistema de compilación. Si vcpkg no encuentra el sistema de compilación especificado en el equipo local, lo descargará e instalará.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

Para los proyectos de CMAKE, use CMAKE_TOOLCHAIN_FILE para que las bibliotecas estén disponibles con `find_package()`. Por ejemplo:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Lista de las bibliotecas ya instaladas

Después de haber instalado algunas bibliotecas, puede usar **vcpkg list** para ver lo que tiene:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>Integración con Visual Studio (Windows)

### <a name="per-user"></a>Por usuario

Ejecute **vcpkg integrate install** para configurar Visual Studio de forma que encuentre todos los archivos de encabezado y binarios de vcpkg de cada usuario sin que sea necesario editar manualmente las rutas de acceso de los directorios de VC++. Si tiene varios clones, el clon desde el que se haya ejecutado este comando se convierte en la nueva ubicación predeterminada.

Ahora podrá incluir encabezados fácilmente escribiendo el encabezado o la carpeta, tarea para la que tendrá la ayuda de la función Autocompletar. No será necesario hacer nada más para vincular a bibliotecas o agregar referencias de proyecto. En la siguiente ilustración se muestra cómo Visual Studio busca encabezados azure-storage-cpp. Vcpkg coloca sus encabezados en la subcarpeta **/installed**, con particiones creadas a partir de la plataforma de destino. En el siguiente diagrama se muestra la lista de los archivos incluidos en la subcarpeta **/was** de la biblioteca:

![Integración de vcpkg e IntelliSense](media/vcpkg-intellisense.png "vcpkg e IntelliSense")

### <a name="per-project"></a>Por proyecto

Si tiene que usar una versión específica de una biblioteca que sea diferente de la de la instancia activa de vcpkg, siga estos pasos:

1. Creación de un nuevo clon de vcpkg
1. Modifique el elemento portfile de la biblioteca para obtener la versión que necesite.
1. Ejecute **vcpkg install \<library>** .
1. Use **vcpkg integrate project** para crear un paquete NuGet que haga referencia a esa biblioteca en cada proyecto.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integración con Visual Studio Code (Linux/MacOS)

Ejecute **vcpkg integrate install** para configurar Visual Studio Code en Linux y MacOS con la ubicación de la inscripción de vcpkg y habilitar IntelliSense en los archivos de código fuente.

## <a name="target-linux-from-windows-via-wsl"></a>Seleccionar Linux como destino desde Windows a través de WSL

Puede generar archivos binarios de Linux desde un equipo Windows mediante el subsistema de Windows para Linux (WSL). Siga las instrucciones para [configurar WSL en Windows 10](/windows/wsl/install-win10) y configurarlo con la [extensión de Visual Studio para Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). Puede colocar todas las bibliotecas compiladas para Windows y Linux en la misma carpeta y acceder a ella desde Windows y WSL.

## <a name="export_binaries_per_project"></a> Exportar archivos binarios y encabezados compilados

Hacer que todos los miembros de un equipo descarguen y compilen bibliotecas no es muy productivo. Un único miembro del equipo puede hacer ese trabajo y, después, usar **vcpkg export** para crear un archivo ZIP de los archivos binarios y los encabezados, o bien un paquete NuGet (hay varios formatos disponibles), que se puede compartir fácilmente con otros miembros del equipo.

## <a name="updateupgrade-installed-libraries"></a>Actualización de las bibliotecas /upgrade instaladas

El catálogo público se mantiene actualizado con las últimas versiones de las bibliotecas. Para averiguar qué biblioteca local no está actualizada, use **vcpkg update**. Cuando esté a punto para actualizar su colección de puertos a la última versión del catálogo público, ejecute el comando **vcpkg upgrade** para descargar y volver a compilar automáticamente una o todas las bibliotecas instaladas que no estén actualizadas.

De forma predeterminada, el comando **upgrade** solo enumera las bibliotecas que no están actualizadas, pero no las actualiza. Para efectuar la actualización, use la opción **--no-dry-run**.

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Opciones de actualización

- **--no-dry-run**  Permite efectuar la actualización. Si no se especifica, el comando solo enumera los paquetes que no estén actualizados.
- **--keep-going**  Permite continuar con la instalación de los paquetes, incluso aunque alguno produzca un error.
- **--triplet \<t>**  Permite establecer el triplo predeterminado para los paquetes incompletos.
- **--vcpkg-root \<path>**  Permite especificar el directorio vcpkg que se usará, en lugar del actual o el de la herramienta.

### <a name="upgrade-example"></a>Ejemplo de actualización

En el ejemplo siguiente se muestra cómo actualizar solo las bibliotecas especificadas. Tenga en cuenta que vcpgk extrae las dependencias automáticamente, según sea necesario.

```cmd
c:\users\satyan\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>Contribución con nuevas bibliotecas

Puede incluir cualquier biblioteca que quiera en la colección de puertos privados. Para sugerir una nueva biblioteca para el catálogo público, abra un problema en la [página de problemas de vcpkg de GitHub](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Quitar una biblioteca

Escriba **vcpkg remove** para quitar una biblioteca instalada. Si hay alguna otra biblioteca que dependa de ella, se le pedirá que vuelva a ejecutar el comando con **--recurse**, lo que hará que todas las de nivel inferior se quiten.

## <a name="customize-vcpkg"></a>Personalización de vcpkg

El clon de vcpkg se puede modificar según sus criterios. Se pueden crear varios clones de vcpkg y modificar los archivos portfile de cada uno de ellos para obtener versiones específicas de bibliotecas o especificar parámetros de línea de comandos. Por ejemplo, en una empresa, un grupo de desarrolladores podría estar trabajando en un software con un conjunto de dependencias, mientras que otro grupo podría tener un conjunto diferente. Se pueden configurar dos clones de vcpkg y modificar cada uno de ellos para descargar las versiones de las bibliotecas y de los modificadores de compilación, etc., según las necesidades.

## <a name="uninstall-vcpkg"></a>Desinstalación de vcpkg

Basta con eliminar el directorio.

## <a name="send-feedback-about-vcpkg"></a>Envío de comentarios sobre vcpkg

Use el comando **vcpkg contact --survey** para enviar comentarios a Microsoft sobre vcpkg, incluidos informes de error y sugerencias para las características.

## <a name="the-vcpkg-folder-hierarchy"></a>Jerarquía de carpetas de vcpkg

Las funcionalidades y los datos de vcpkg son independientes entre sí dentro de la misma jerarquía de directorios, característica que se denomina "instancia". No hay ninguna configuración del Registro ni variables de entorno. Puede haber cualquier número de instancias de vcpkg en un equipo, y estas no interferirán entre sí.

El contenido de una instancia de vcpkg es:

- buildtrees: Contiene subcarpetas con los orígenes a partir de los cuales se compila cada biblioteca.
- docs: Documentación y ejemplos.
- donwloads: Copias almacenadas en caché de las herramientas u orígenes descargados. Aquí es donde vcpkg busca en primer lugar cuando se ejecuta el comando de instalación.
- installed: Contiene los encabezados y los archivos binarios de cada biblioteca instalada. Al realizar la integración con Visual Studio, básicamente lo que se está indicando es que se agregue una carpeta determinada a las rutas de acceso de búsqueda.
- packages: Carpeta interna para el almacenamiento provisional entre instalaciones.
- ports: Archivos que describen cada biblioteca en el catálogo, su versión y dónde descargarla. Puede agregar sus propios puertos si es necesario.
- scripts: Scripts (cmake, powershell) usados por vcpkg.
- toolsrc: Código fuente de C++ relativo a vcpkg y a los componentes relacionados.
- triplets: Contiene la configuración de cada plataforma de destino admitida (p. ej., x86-windows o x64-uwp).

## <a name="command-line-reference"></a>Referencia de la línea de comandos

|Comando|Descripción|
|---------|---------|
|**vcpkg search [pat]**|Permite buscar los paquetes disponibles para instalar.|
|**vcpkg install \<pkg>...**|Instala un paquete.|
|**vcpkg remove \<pkg>...**|Desinstala un paquete.|
|**vcpkg remove --outdated**|Permite desinstalar todos los paquetes que no estén actualizados.|
|**vcpkg list**|Permite enumerar los paquetes instalados.|
|**vcpkg update**|Permite mostrar una lista de los paquetes que deben actualizarse.|
|**vcpkg upgrade**|Permite volver a compilar todos los paquetes que no estén actualizados.|
|**vcpkg hash \<file> [alg]**|Permite usar un algoritmo hash específico en un archivo. El predeterminado es SHA512.|
|**vcpkg integrate install**|Permite poner los paquetes instalados a disposición de todos los usuarios. Requiere privilegios de administrador en el primer uso.|
|**vcpkg integrate remove**|Permite quitar la integración con todos los usuarios.|
|**vcpkg integrate project**|Permite generar un paquete NuGet de referencia para uso individual de un proyecto de VS.|
|**vcpkg export \<pkg>... [opt]...**|Permite exportar un paquete.|
|**vcpkg edit \<pkg>**|Permite abrir un puerto para editarlo (usa %EDITOR%, predeterminado: "code").|
|**vcpkg create \<pkg> \<url> [archivename]**|Permite crear un nuevo paquete.|
|**vcpkg cache**|Permite enumerar los paquetes compilados almacenados en la memoria caché.|
|**vcpkg version**|Permite mostrar la información de la versión.|
|**vcpkg contact --survey**|Permite mostrar información de contacto para enviar comentarios.|

### <a name="options"></a>Opciones

|Opción|Descripción|
|---------|---------|
|**--triplet \<t>**|Permite especificar el triplo de la arquitectura de destino. El valor predeterminado es `%VCPKG_DEFAULT_TRIPLET%`; vea también **vcpkg help triplet**.|
|**--vcpkg-root \<path>**|Permite especificar el directorio raíz de vcpkg. El predeterminado es `%VCPKG_ROOT%`.|
