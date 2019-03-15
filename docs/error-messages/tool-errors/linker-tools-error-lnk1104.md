---
title: Error de las herramientas del vinculador LNK1104
ms.date: 05/17/2017
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: eadeeb7ac19e3975a37a1364502b33400018cb05
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818276"
---
# <a name="linker-tools-error-lnk1104"></a>Error de las herramientas del vinculador LNK1104

> no se puede abrir el archivo '*filename*'

El vinculador no pudo abrir el archivo especificado. Las causas más comunes de este problema son que el archivo está en uso o bloqueado por otro proceso, no existe, no se encuentra en uno de los directorios que el vinculador busca, o puede que no tenga permisos suficientes para tener acceso al archivo. Con menos frecuencia, puede haberse quedado sin espacio en disco, el archivo puede ser demasiado grande o la ruta de acceso al archivo puede ser demasiado larga.

## <a name="possible-causes-and-solutions"></a>Las posibles causas y soluciones

Este error puede producirse cuando el vinculador intenta abrir un archivo para lectura o escritura. Para restringir las causas posibles, compruebe qué tipo de archivo se encuentra y use las secciones siguientes para ayudar a identificar y corregir el problema específico.

### <a name="cannot-open-your-app-or-its-pdb-file"></a>No se puede abrir la aplicación o su archivo .pdb

Si el nombre de archivo es el ejecutable compila el proyecto o un archivo .pdb asociado, la causa más común es que la aplicación ya se está ejecutando cuando se intenta volver a generarlo o se carga en un depurador. Para corregir este problema, detenga el programa y se descarga desde el depurador antes de volver a compilar. Si la aplicación está abierta en otro programa, por ejemplo, un editor de recursos, ciérrelo. En casos extremos, necesita usar el Administrador de tareas para finalizar el proceso, o detenga y reinicie Visual Studio.

Los programas antivirus a menudo temporalmente bloquear el acceso a los archivos recién creados especialmente .exe y .dll archivos ejecutables. Para corregir este problema, intente excluir los directorios de compilación del proyecto de la detección de virus.

### <a name="cannot-open-a-microsoft-library-file"></a>No se puede abrir un archivo de Microsoft Library

Si el archivo que no se puede abrir uno de los archivos de biblioteca estándar proporcionados por Microsoft, por ejemplo, kernel32.lib, es posible tener un error de configuración de proyecto o un error de instalación. Compruebe que se ha instalado el SDK de Windows y si el proyecto requiere otras bibliotecas de Microsoft, tales como MFC, asegúrese de que los componentes MFC también se han instalado por el instalador de Visual Studio. Puede ejecutar el instalador de nuevo para agregar componentes opcionales en cualquier momento. Para obtener más información, consulte [modificar Visual Studio](/visualstudio/install/modify-visual-studio). Utilice la pestaña componentes individuales en el instalador para elegir determinadas bibliotecas y SDK.

Si va a compilar un proyecto que se creó con una versión anterior de Visual Studio, pueden no instalarse el conjunto de herramientas de plataforma y bibliotecas para esa versión. Si el mensaje de error se produce para un nombre de biblioteca con control de versiones, como msvcr100.lib, esta es probablemente la causa. Para corregir este problema, tiene dos opciones: puede actualizar el proyecto para usar el conjunto de herramientas de plataforma actual ha instalado, o puede instalar el conjunto de herramientas anterior y compile el proyecto sin cambios. Para obtener más información, consulte [actualizar proyectos desde versiones anteriores de Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) y [utilizar nativa con múltiples versiones de Visual Studio para compilar proyectos antiguos](../../porting/use-native-multi-targeting.md).

Si ve este error al compilar para una nueva plataforma de destino o la configuración, las bibliotecas para ese conjunto de herramientas de plataforma o configuración de proyecto no pueden instalarse. Compruebe que la **conjunto de herramientas de plataforma** y **versión del SDK de Windows** especificado en el [página de propiedades General](../../build/reference/general-property-page-project.md) están instalados para el proyecto y compruebe que los necesarios las bibliotecas están disponibles en el **directorios de bibliotecas** especificado en el [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) para las opciones de configuración. Hay configuraciones independientes para la depuración y las configuraciones de venta directa, así como las configuraciones de 32 bits y 64 bits, por lo que si una compilación funciona pero sí produce un error, asegúrese de que la configuración es correcta y se instalan las bibliotecas y herramientas necesarias para cada compilar la configuración.

Si usas el IDE de Visual Studio para compilar un proyecto que se copió desde otro equipo, las ubicaciones de instalación para las bibliotecas pueden variar. Compruebe el **directorios de bibliotecas** propiedad en el [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) para el proyecto y actualizarla si es necesario. Para ver y editar las rutas de acceso de biblioteca actual establecidos en el IDE, elija el control de lista desplegable para la **directorios de bibliotecas** propiedad y elija **editar**. El **evalúa el valor** sección de la **directorios de bibliotecas** cuadro de diálogo enumera las rutas de acceso actuales a buscar archivos de biblioteca.

Este error también puede producirse cuando la ruta de acceso al SDK de Windows no está actualizada. Si ha instalado una versión del SDK de Windows más reciente que la versión de Visual Studio, asegúrese de que las rutas de acceso especifican en el [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) se actualizan para que coincida con el nuevo SDK. Si usa el símbolo del sistema para desarrolladores, asegúrese de que se actualiza el archivo por lotes que inicializa las variables de entorno para las nuevas rutas SDK. Este problema puede evitarse mediante el instalador de Visual Studio para instalar el SDK actualizados.

### <a name="cannot-open-a-third-party-library-file"></a>No se puede abrir un archivo de biblioteca de terceros

Hay varias causas para este problema:

- La ruta de acceso al archivo de biblioteca puede ser incorrecto o que no haya especificado el vinculador.

- Es posible que ha instalado una versión de 32 bits de la biblioteca, pero va a compilar para 64 bits, o viceversa.

- La biblioteca puede tener dependencias en otras bibliotecas que no están instalados.

Para corregir un problema de la ruta de acceso, compruebe que la variable de entorno LIB está establecida y contiene todos los directorios para las bibliotecas que usa para todas las configuraciones que compila. En el IDE, se establece la variable LIB el **directorios de bibliotecas** propiedad en el [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md). Asegúrese de que todos los directorios que contienen las bibliotecas que necesarias se muestran aquí, para cada configuración que cree.

Si tiene que proporcionar un directorio de biblioteca que invalida un directorio de la biblioteca estándar, puede usar el [/libpath](../../build/reference/libpath-additional-libpath.md) opción en la línea de comandos, o en el IDE, puede usar el **directorios de bibliotecas adicionales** propiedad en el **propiedades de configuración > vinculador > General** página de propiedades para el proyecto.

Asegúrese de que ha instalado todas las versiones de la biblioteca que necesita para las configuraciones de que compilar. Considere el uso de la [vcpkg](../../vcpkg.md) utilidad de administración para automatizar la instalación y configuración de muchas bibliotecas comunes de paquetes. Cuando sea posible, es mejor crear sus propias copias de las bibliotecas de terceros, por lo que está seguro de que todas las dependencias locales que requieren las bibliotecas y que se compilan para la misma configuración que el proyecto.

### <a name="cannot-open-a-file-built-by-your-project"></a>No se puede abrir un archivo compilado en el proyecto

Puede ver este error si el archivo *filename* se compila la solución, pero aún no existe cuando el vinculador intenta obtener acceso a él. Esto puede ocurrir cuando un proyecto depende de otro proyecto, pero no se compilan los proyectos en el orden correcto. Para corregir este problema, asegúrese de que las referencias del proyecto se establecen en el proyecto que usa el archivo, por lo que el archivo que falta se compila antes de que sea necesario. Para obtener más información, consulte [agregar referencias en proyectos de Visual C++](../../build/adding-references-in-visual-cpp-projects.md) y [administrar referencias en un proyecto](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>No se puede abrir el archivo ' C:\\Program.obj'

Si ve este error, o un error similar que implican un archivo .obj inesperado en la raíz de la unidad, el problema es casi seguro que una ruta de acceso de biblioteca que no se ajusta en comillas dobles.

Para corregir este problema para las compilaciones de línea de comandos, compruebe el [/libpath](../../build/reference/libpath-additional-libpath.md) opción parámetros, las rutas especificadas en la variable de entorno LIB y las rutas de acceso especificadas en la línea de comandos y asegúrese de utilizar comillas dobles alrededor de las rutas de acceso que incluyen espacios.

Para corregir este problema en el IDE, compruebe el **directorios de bibliotecas** propiedad en el [propiedades de configuración > directorios de VC ++](../../build/reference/vcpp-directories-property-page.md) página de propiedades, el **dedirectoriosdebibliotecasadicionales** propiedad en el **propiedades de configuración > vinculador > General** página de propiedades y el **dependencias adicionales** propiedad en el **configuración Propiedades > vinculador > entrada** página de propiedades para el proyecto. Asegúrese de que todas las rutas de acceso de directorio que contienen las bibliotecas que necesarias se encapsulan en comillas dobles si es necesario.

### <a name="other-common-issues"></a>Otros problemas comunes

Este error puede producirse cuando se especifica el nombre de archivo de biblioteca o una ruta de acceso al enlazador en la línea de comandos o en un [#pragma comment (lib, "nombre_de_biblioteca")](../../preprocessor/comment-c-cpp.md) directiva es incorrecta o la ruta de acceso tiene una especificación de unidad no válida. Compruebe la ortografía y la extensión de archivo y que el archivo existe en la ubicación especificada.

Puede que otro programa tenga el archivo abierto y que el enlazador no puede escribir en él. Los programas antivirus a menudo bloquean temporalmente el acceso a archivos recién creados. Para corregir este problema, intente excluir los directorios de compilación del proyecto de la detección de virus.

Si usa una opción de compilación paralela, es posible que Visual Studio ha bloqueado el archivo en otro subproceso. Para corregir este problema, compruebe que no genera el mismo objeto de código o la biblioteca en varios proyectos y usar dependencias de compilación o referencias de proyecto para recoger archivos binarios compilados en el proyecto.

Al especificar bibliotecas individuales en el **dependencias adicionales** propiedad directamente, use espacios para separar los nombres de biblioteca, no comas o punto y coma. Si usas el **editar** elemento de menú para abrir el **dependencias adicionales** cuadro de diálogo, use las nuevas líneas para separar los nombres, no por comas, puntos y comas o espacios. Usar también las nuevas líneas al especificar las rutas de acceso de biblioteca en el **directorios de bibliotecas** y **directorios de bibliotecas adicionales** cuadros de diálogo.

Puede ver este error cuando la ruta de acceso *filename* más de 260 caracteres. Cambiar los nombres o reorganizar la estructura de directorios si es necesario para acortar las rutas de acceso a los archivos necesarios.

Este error puede producirse porque el archivo es demasiado grande. Las bibliotecas u objeto archivos de más de un gigabyte de tamaño puede causar problemas para el enlazador de 32 bits. Una posible solución para este problema es usar el conjunto de herramientas de 64 bits. Para obtener más información sobre cómo hacerlo en la línea de comandos, vea [Cómo: Habilitar un Toolset de 64 bits Visual C++ en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Para obtener información sobre cómo hacer esto en el IDE, vea [utilizar MSBuild con el compilador de 64 bits y herramientas](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) y esta entrada de Stack Overflow: [Cómo hacer que Visual Studio utiliza la cadena de herramientas nativo amd64](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

Este error puede producirse si tiene permisos de archivo insuficientes para tener acceso a *filename*. Esto puede ocurrir si usar una cuenta de usuario normal y el intento de obtener acceso a archivos de biblioteca en los directorios del sistema protegidos o usar los archivos copiados a otros usuarios que tienen los permisos originales establecido. Para corregir este problema, mueva el archivo a un directorio de proyecto grabable. Si el archivo se encuentra en un directorio de escritura, pero tiene permisos de acceso, puede usar un símbolo del sistema de administrador y ejecute el comando de takeown.exe tomar posesión del archivo.

El error puede producirse cuando no hay suficiente espacio en disco. El enlazador usa archivos temporales en varios casos. Aunque tenga suficiente espacio en disco, un vínculo muy grande puede agotar o fragmentar el espacio en disco disponible. Considere el uso de la [/OPT (optimizaciones)](../../build/reference/opt-optimizations.md) opción; la realización de lecturas de eliminación de COMDAT transitivas todos los archivos objeto varias veces.

Si el *filename* se denomina LNK*nnn*, que es un nombre de archivo generado por el enlazador para un archivo temporal, el directorio especificado en la variable de entorno TMP no exista, o puede ser más de un directorio especificado para la variable de entorno TMP. Debe especificarse la ruta de acceso de un único directorio para la variable de entorno TMP.
