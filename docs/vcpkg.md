---
title: 'Vcpkg: Administrador de paquetes de C++ para Windows | Microsoft Docs'
description: "Vcpkg es un administrador de paquetes de la línea de comandos que simplifica en gran medida la adquisición e instalación de bibliotecas de C++ de código abierto en Windows."
keywords: vcpkg
author: mikeblome
ms.author: mblome
ms.date: 05/30/2017
ms.technology:
- cpp-ide
ms.tgt_pltfrm: windows
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.topic: article
dev_langs:
- C++
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: ed0e4505b68c2ea198e0771b6301e685daa8662e
ms.openlocfilehash: de5825e64abac210561cb8cbe0dc3320a740cbee
ms.contentlocale: es-es
ms.lasthandoff: 06/30/2017

---

# <a name="vcpkg-c-package-manager-for-windows"></a>Vcpkg: Administrador de paquetes de C++ para Windows 
Vcpkg es un administrador de paquetes de la línea de comandos que simplifica en gran medida la adquisición e instalación de bibliotecas de terceros en Windows. Si se usan bibliotecas de terceros en el proyecto, conviene usar vcpkg para instalarlas. Vcpkg admite bibliotecas tanto de código abierto como propietarias. Todas las bibliotecas contenidas en el catálogo público de vcpkg se han sometido a pruebas para confirmar su compatibilidad con Visual Studio 2015 y Visual Studio 2017. Con fecha de mayo de 2017, existen alrededor de 238 bibliotecas en el catálogo, y la comunidad de C++ sigue agregando más de forma constante.

## <a name="simple-yet-flexible"></a>Simple, pero flexible
Con un solo comando se pueden descargar orígenes y compilar una biblioteca. Vcpkg es, en sí mismo, un proyecto de código abierto disponible en GitHub. Puede personalizar su clones privados de la forma que quiera. Así, por ejemplo, puede especificar diferentes bibliotecas o distintas versiones de las bibliotecas que figuran en el catálogo público. Puede tener varios clones de vcpkg en un mismo equipo y que cada uno de ellos genere conjuntos personalizados de bibliotecas o conmutadores de compilación, etc. Cada clon es un entorno completamente autónomo y susceptible de copiarse mediante XCOPY y, como tal, posee su propia copia de vcpkg.exe que funciona únicamente en su propia jerarquía. Vcpkg no se agrega a ninguna variable de entorno y no tiene ninguna dependencia en el Registro de Windows ni en Visual Studio.

## <a name="sources-not-binaries"></a>Orígenes no binarios
Vcpkg descarga orígenes en lugar de archivos binarios[1] para las bibliotecas del catálogo público. También permite compilar esos orígenes con Visual Studio 2017, o bien con Visual Studio 2015 si la versión 2017 no está instalada. En C++, es muy importante las bibliotecas que se usen se hayan compilado con el mismo compilador y la misma versión de compilador que el código de la aplicación que vincula. Al usar vcpkg, se elimina (o, al menos, se reduce considerablemente) la posibilidad de que haya una discrepancia en los archivos binarios y los problemas que pueden derivarse de esto. En los equipos que suelen usar una versión específica del compilador de Visual C++, un miembro del equipo puede usar vcpkg para descargar orígenes y compilar un conjunto de archivos binarios y, después, usar el comando de exportación para comprimir esos archivos binarios y los encabezados para otros miembros del equipo. Para más información, consulte Exportación de encabezados y archivos binarios compilados más adelante. 

Si crea un clon de vcpkg con bibliotecas privadas en la colección de puertos, puede agregar un puerto que descargue encabezados y archivos binarios ya creados previamente y escribir un archivo portfile.cmake que, simplemente, copie tales archivos en la ubicación que quiera.

[1] *Nota: En el caso de algunas bibliotecas propietarias, no hay ningún origen disponible. En tal caso, vcpkg descargará archivos binarios creados previamente compatibles.*

## <a name="installation"></a>Instalación
Clone el repositorio de vcpkg desde GitHub: https://github.com/Microsoft/vcpkg. Puede descargarlo en la ubicación de carpeta que prefiera.

Ejecute el programa previo en la carpeta raíz: bootstrap-vcpkg.bat.

## <a name="basic-tasks"></a>Tareas básicas
  
### <a name="search-the-list-of-available-libraries"></a>Búsqueda en la lista de bibliotecas disponibles
Para ver qué paquetes hay disponibles, escriba lo siguiente en el símbolo del sistema: `vcpkg search`.

Con este comando se enumeran los archivos de control contenidos en las subcarpetas vcpkg/ports. La lista será similar a la siguiente:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. <https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

  Puede filtrar según un patrón, por ejemplo, `vcpkg search ta`:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library

```

### <a name="install-a-library-on-your-local-machine"></a>Instalación de una biblioteca en el equipo local
Tras obtener el nombre de una biblioteca por medio de `vcpkg search`, hay que usar `vcpkg install` para descargar la biblioteca y compilarla. Vcpkg usa el archivo portfile de la biblioteca en el directorio ports. Si no se especifica ningún triplo, vcpkg instalará y compilará para Windows x86. Si en el archivo portfile hay especificada alguna dependencia, vcpkg la descargará e instalará también. Tras la descarga, vcpkg compila la biblioteca usando el sistema de compilación que la biblioteca use. Aunque se prefieren los archivos de proyecto CMake y MSBuild, MAKE también se admite junto con cualquier otro sistema de compilación. Si vcpkg no encuentra el sistema de compilación especificado en el equipo local, lo descargará e instalará.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

### <a name="list-the-libraries-already-installed"></a>Lista de las bibliotecas ya instaladas
Después de haber instalado algunas bibliotecas, puede usar `vcpkg list` para ver lo que tiene:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

### <a name="integrate-with-visual-studio"></a>Integración con Visual Studio
#### <a name="per-user"></a>Por usuario
Ejecute `vcpkg integrate install` para configurar Visual Studio de forma que encuentre todos los archivos de encabezado y binarios de vcpkg de cada usuario sin que sea necesario editar manualmente las rutas de acceso de los directorios de VC++. Si tiene varios clones, el clon desde el que se haya ejecutado este comando se convierte en la nueva ubicación predeterminada.

Ahora podrá incluir encabezados sencillamente escribiendo el encabezado o la carpeta, tarea para la que tendrá la ayuda de la función Autocompletar. No será necesario hacer nada más para vincular a bibliotecas o agregar referencias de proyecto. En la siguiente ilustración se muestra cómo Visual Studio busca encabezados azure-storage-cpp. Vcpkg coloca sus encabezados en la subcarpeta \installed, con particiones creadas a partir de la plataforma de destino. En el siguiente diagrama se muestra la lista de archivos de inclusión en la subcarpeta `/was` de la biblioteca:

 ![Integración de vcpkg e Intellisense](media/vcpkg-intellisense.png "vcpkg e Intellisense")  

#### <a name="per-project"></a>Por proyecto
Si tiene que usar una versión específica de una biblioteca distinta de la versión de la instancia de vcpkg activa, puede crear un clon de vcpkg, modificar el archivo portfile para que la biblioteca obtenga la versión que necesita y, luego, ejecutar `vcpkg install <library>`. Después, puede usar `vcpkg integrate project` para crear un paquete NuGet que haga referencia a esa biblioteca en cada proyecto.

### <a name="export-compiled-binaries-and-headers"></a>Exportación de encabezados y archivos binarios compilados
Hacer que todos los miembros de un equipo descarguen y compilen bibliotecas no es muy productivo. Uno de ellos podría encargarse de esa tarea y, luego, usar `vcpkg export` para crear un archivo .zip con los archivos binarios y los encabezados que pueda compartirse fácilmente con el resto de miembros del equipo. 

### <a name="update-installed-libraries"></a>Actualización de las bibliotecas instaladas
El catálogo público se mantiene actualizado con las últimas versiones de las bibliotecas. Para averiguar qué biblioteca local no está actualizada, use `vcpkg update`. Cuando esté listo para actualizar la colección de puertos a la versión más reciente del catálogo público, basta con realizar una operación git pull en el repositorio de Github o crear un clon y conservar el antiguo, si fuera necesario.

### <a name="contribute-new-libraries"></a>Contribución con nuevas bibliotecas
Puede incluir cualquier biblioteca que quiera en la colección de puertos privados. Para sugerir una nueva biblioteca para el catálogo público: 


### <a name="remove-a-library"></a>Quitar una biblioteca
Escriba `vcpkg remove` para quitar una biblioteca instalada. Si hay alguna otra biblioteca que dependa de ella, se le pedirá que vuelva a ejecutar el comando con `--recurse`, lo que hará que todas las bibliotecas de nivel inferior se quiten.

### <a name="customize-vcpkg"></a>Personalización de vcpkg
El clon de vcpkg se puede modificar según sus criterios. Se pueden crear varios clones de vcpkg y modificar los archivos portfile de cada uno de ellos para obtener versiones específicas de bibliotecas o especificar parámetros de línea de comandos. Por ejemplo, en una empresa, un grupo de desarrolladores podría estar trabajando en un software con un conjunto de dependencias, mientras que otro grupo podría tener un conjunto diferente. En esta situación, se pueden configurar dos clones de vcpkg y modificar cada uno de ellos para descargar las versiones de las bibliotecas y de los conmutadores de compilación, etc. acordes a las necesidades de cada uno. 

## <a name="the-vcpkg-folder-hierarchy"></a>Jerarquía de carpetas de vcpkg
Todas las funcionalidades y datos de vcpkg son completamente independientes entre sí dentro de la misma jerarquía de directorios; esto es lo que se denomina "instancia". No hay ninguna configuración del Registro ni variables de entorno. Puede haber cualquier número de instancias de vcpkg en un equipo, que no interferirán entre sí. 

El contenido de una instancia de vcpkg es: 
- buildtrees: Contiene subcarpetas con los orígenes a partir de los cuales se compila cada biblioteca.
- docs: Documentación y ejemplos.
- donwloads: Copias almacenadas en caché de las herramientas u orígenes descargados. Aquí es donde vcpkg busca en primer lugar cuando se ejecuta el comando de instalación.
- installed: Contiene los encabezados y los archivos binarios de cada biblioteca instalada. Al integrar con Visual Studio, básicamente lo que se está indicando es que se agregue una carpeta determinada a las rutas de acceso de búsqueda.
- packages: Carpeta interna para el almacenamiento provisional entre instalaciones.
- ports: Archivos que describen cada biblioteca en el catálogo, su versión y dónde descargarla. Puede agregar sus propios puertos si es necesario.
- scripts: Scripts (cmake, powershell) usados por vcpkg.
- toolsrc: Código fuente de C++ relativo a vcpkg y a los componentes relacionados.
- triplets: Contiene la configuración de cada plataforma de destino admitida (p. ej., x86-windows o x64-uwp).

## <a name="command-line-reference"></a>Referencia de la línea de comandos
- vcpkg search [pat]       Busca los paquetes disponibles para compilarse.
- vcpkg install <pkg>...    Instala un paquete.
- vcpkg remove <pkg>...  Desinstala un paquete.
- vcpkg remove --outdated   Desinstala todos los paquetes obsoletos.
- vcpkg list            Enumera los paquetes instalados.
- vcpkg update          Muestra una lista de los paquetes que deben actualizarse.
- vcpkg hash <file> [alg]       Usa un algoritmo hash específico (predeterminado: SHA512) en un archivo.
- vcpkg integrate install       Pone los paquetes instalados a disposición de todos los usuarios. Requiere privilegios de administrador en el primer uso.
- vcpkg integrate remove        Quita la integración de todos los usuarios.
- vcpkg integrate project        Genera un paquete NuGet de referencia para uso individual de un proyecto de VS.
- vcpkg export <pkg>... [opt]...    Exporta un paquete.
- vcpkg edit <pkg>      Abre un puerto para editarlo (usa %EDITOR%, predeterminado: 'code').
- vcpkg import <pkg>        Importa una biblioteca precompilada.
- vcpkg create <pkg> <url>   [archivename]        Crea un paquete.
- vcpkg owns <pat>      Busca archivos en los paquetes instalados.
- vcpkg cache           Enumera los paquetes compilados almacenados en la memoria caché.
- vcpkg version         Muestra la información de versión.
- vcpkg contact         Muestra información de contacto para enviar comentarios.

### <a name="options"></a>Opciones:
  **`--triplet <t>`** Especifica el triplo de la arquitectura de destino. (predeterminado: `%VCPKG_DEFAULT_TRIPLET%`, vea también `vcpkg help triplet`).

  **`--vcpkg-root <path>`** Especifica el directorio raíz de vcpkg (predeterminado: `%VCPKG_ROOT%`).

