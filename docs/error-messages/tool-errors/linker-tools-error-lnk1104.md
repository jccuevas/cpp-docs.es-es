---
title: Error de las herramientas del vinculador LNK1104
description: Describe el LNK1104 de errores C++ del enlazador C y (MSVC) de Microsoft, sus causas y posibles soluciones.
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: 8878db1b0829703b22b2f7863eb7955d17ad3096
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301787"
---
# <a name="linker-tools-error-lnk1104"></a>Error de las herramientas del vinculador LNK1104

> no se puede abrir el archivo '*nombreDeArchivo*'

Este error se genera cuando el vinculador no puede abrir un archivo, ya sea para lectura o para escritura. Las dos causas más comunes del problema son las siguientes:

- el programa ya se está ejecutando o está cargado en el depurador, y

- las rutas de acceso de la biblioteca son incorrectas o no se incluyen entre comillas dobles.

Hay muchas otras causas posibles de este error. Para reducirlos, compruebe primero qué tipo de *nombre* de archivo es. A continuación, use las secciones siguientes para ayudar a identificar y corregir el problema específico.

## <a name="cant-open-your-app-or-its-pdb-file"></a>No se puede abrir la aplicación ni su archivo. pdb

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>La aplicación se está ejecutando o está cargada en el depurador

Cuando *filename* es el nombre del archivo ejecutable o un archivo. pdb asociado, vea si la aplicación ya se está ejecutando. A continuación, compruebe si se ha cargado en un depurador. Para corregir este problema, detenga el programa y descárguelo del depurador antes de compilarlo de nuevo. Si la aplicación está abierta en otro programa, como un editor de recursos, ciérrela. Si el programa no responde, puede que tenga que usar el administrador de tareas para finalizar el proceso. También podría necesitar cerrar y reiniciar Visual Studio.

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>La aplicación está bloqueada por un examen antivirus

Los programas antivirus suelen bloquear temporalmente el acceso a los archivos recién creados, especialmente a los archivos ejecutables. exe y. dll. Para solucionar este problema, pruebe a excluir los directorios de compilación del proyecto del detector de virus.

## <a name="cant-open-a-microsoft-library-file"></a>No se puede abrir un archivo de biblioteca de Microsoft

### <a name="windows-libraries-such-as-kernel32lib"></a>Bibliotecas de Windows, como Kernel32. lib

Si el archivo que no se puede abrir es uno de los archivos de la biblioteca estándar que proporciona Microsoft, como *Kernel32. lib*, puede tener un error de configuración del proyecto o un error de instalación. Compruebe que se ha instalado el Windows SDK. Si el proyecto requiere otras bibliotecas de Microsoft, como MFC, asegúrese de que los componentes de MFC también se instalaron con el instalador de Visual Studio. Puede volver a ejecutar el instalador para agregar componentes opcionales en cualquier momento. Para obtener más información, vea [modificar Visual Studio](/visualstudio/install/modify-visual-studio). Use la pestaña **componentes individuales** del instalador para elegir bibliotecas y SDK específicos.

### <a name="versioned-vcruntime-libraries"></a>Bibliotecas de vcruntime de versiones

Si el mensaje de error tiene una biblioteca de Microsoft con versión, como *msvcr120. lib*, es posible que el conjunto de herramientas de la plataforma para esa versión del compilador no esté instalado. Para corregir este problema, tiene dos opciones: actualizar el proyecto para usar el conjunto de herramientas de la plataforma actual o instalar el conjunto de herramientas anterior y compilar el proyecto sin cambios. Para obtener más información, vea [actualizar proyectos de versiones anteriores de Visual C++ ](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) y [usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos](../../porting/use-native-multi-targeting.md).

### <a name="retail-debug-or-platform-specific-libraries"></a>Bibliotecas de venta directa, depuración o específicas de la plataforma

El error puede producirse al compilar por primera vez una nueva plataforma o configuración de destino, como venta directa o ARM64. En el IDE, compruebe que el **conjunto de herramientas** de la plataforma y la versión de **Windows SDK** especificada en la [Página de propiedades general](../../build/reference/general-property-page-project.md) están instaladas. Compruebe también que las bibliotecas necesarias están disponibles en los **directorios de biblioteca** especificados en la página de [propiedades directorios de VC + +](../../build/reference/vcpp-directories-property-page.md). Compruebe las propiedades de cada configuración, como depurar, venta directa, x86 o ARM64. Si una compilación funciona pero otra no, compare la configuración de ambos. Instale las herramientas y bibliotecas necesarias que falten.

### <a name="the-vccorliblib-library"></a>La biblioteca vccorlib. lib

No hay ninguna biblioteca Spectre para los componentes o aplicaciones universales de Windows (UWP). Si el mensaje de error incluye *vccorlib. lib*, es posible que haya habilitado [/Qspectre](../../build/reference/qspectre.md) en un proyecto de UWP. Deshabilite la opción del compilador **/Qspectre** para corregir este problema. En Visual Studio, cambie la propiedad de **mitigación Spectre** . Se encuentra en la página **generación de código** de **CC++ /**  > del cuadro de diálogo páginas de **propiedades** del proyecto.

### <a name="libraries-in-projects-from-online-or-other-sources"></a>Bibliotecas en proyectos de otros orígenes en línea

Si compila un proyecto copiado desde otro equipo, las ubicaciones de instalación de la biblioteca pueden ser diferentes. En el caso de las compilaciones de línea de comandos, compruebe que la variable de entorno LIB y las rutas de acceso de biblioteca están establecidas correctamente para la compilación. En Visual Studio, puede ver y editar las rutas de acceso de biblioteca actuales establecidas en las páginas de propiedades del proyecto. En la página **directorios de VC + +** , elija el control desplegable de la propiedad **directorios de biblioteca** y, a continuación, elija **Editar**. En la sección **valor evaluado** del cuadro de diálogo **directorios de biblioteca** se muestran las rutas de acceso actuales que se buscan en los archivos de biblioteca. Actualice estas rutas de acceso para que apunten a las bibliotecas locales.

### <a name="updated-windows-sdk-libraries"></a>Bibliotecas de Windows SDK actualizadas

Este error puede producirse si la ruta de acceso de Visual Studio al Windows SDK no está actualizada. Puede ocurrir si instala una Windows SDK más reciente independientemente del instalador de Visual Studio. Para corregirlo en el IDE, actualice las rutas de acceso especificadas en la [Página de propiedades directorios de VC + +](../../build/reference/vcpp-directories-property-page.md). Establezca la versión de la ruta de acceso para que coincida con el nuevo SDK. Si usa el Símbolo del sistema para desarrolladores, actualice el archivo por lotes que inicializa las variables de entorno con las nuevas rutas de acceso del SDK. Este problema se puede evitar mediante el instalador de Visual Studio para instalar los SDK actualizados.

## <a name="cant-open-a-third-party-library-file"></a>No se puede abrir un archivo de biblioteca de otro fabricante

Hay varias causas comunes para este problema:

- La ruta de acceso al archivo de biblioteca puede ser incorrecta o no debe incluirse entre comillas dobles. O bien, es posible que no se haya especificado en el enlazador.

- Es posible que haya instalado una versión de 32 bits de la biblioteca, pero está compilando para 64 bits o de otra manera.

- La biblioteca puede tener dependencias en otras bibliotecas que no están instaladas.

Para corregir un problema de ruta de acceso para las compilaciones de línea de comandos, compruebe que la variable de entorno LIB está establecida. Asegúrese de que incluye rutas de acceso para todas las bibliotecas que usa y para cada configuración que cree. En el IDE, las rutas de acceso de biblioteca se establecen mediante los **directorios de VC + +**  > propiedad **directorios de biblioteca** . Asegúrese de que todos los directorios que contienen las bibliotecas que necesita aparecen aquí, para cada configuración que cree.

Es posible que tenga que proporcionar un directorio de biblioteca que invalide un directorio de biblioteca estándar. En la línea de comandos, use la opción [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . En el IDE, use la propiedad **directorios de biblioteca adicionales** en las **propiedades de configuración > enlazador >** página de propiedades general del proyecto.

Asegúrese de instalar todas las versiones de la biblioteca que necesita para las configuraciones que cree. Considere la posibilidad de usar la utilidad de administración de paquetes [vcpkg](../../vcpkg.md) para automatizar la instalación y la configuración de muchas bibliotecas comunes. Cuando sea posible, es mejor crear sus propias copias de bibliotecas de terceros. A continuación, asegúrese de tener todas las dependencias locales de las bibliotecas, compiladas para la misma configuración que el proyecto.

## <a name="cant-open-a-file-built-by-your-project"></a>No se puede abrir un archivo compilado por el proyecto

Puede ver este error si el *nombre de archivo* no existe aún cuando el enlazador intenta tener acceso a él. Puede suceder cuando un proyecto depende de otro en la solución, pero los proyectos se compilan en el orden equivocado. Para corregir este problema, asegúrese de que las referencias del proyecto estén establecidas en el proyecto que utiliza el archivo. Después, el archivo que falta se compila antes de que sea necesario. Para obtener más información, vea [Agregar referencias en proyectos C++ de Visual Studio](../../build/adding-references-in-visual-cpp-projects.md) y [administrar referencias en un proyecto](/visualstudio/ide/managing-references-in-a-project).

## <a name="cannot-open-file-cprogramobj"></a>No se puede abrir el archivo ' C:\\Program. obj '

Si ve el nombre de archivo *C:\\Program. obj* en el mensaje de error, ajuste las rutas de acceso de la biblioteca entre comillas dobles. Este error se produce cuando se pasa al enlazador una ruta de acceso desempaquetada que comienza con *C:\\archivos de programa* . Las rutas de acceso desempaquetadas también pueden producir errores similares. Normalmente, muestran un archivo. obj inesperado en la raíz de la unidad.

Para corregir este problema en las compilaciones de línea de comandos, compruebe los parámetros de la opción [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . Compruebe también las rutas de acceso especificadas en la variable de entorno LIB y las rutas de acceso especificadas en la línea de comandos. Asegúrese de usar comillas dobles alrededor de cualquier ruta de acceso que incluya espacios.

Para corregir este problema en el IDE, agregue comillas dobles según sea necesario a las siguientes propiedades del proyecto:

- La propiedad **directorios de biblioteca** de las propiedades de configuración > Página de propiedades directorios de [VC + +](../../build/reference/vcpp-directories-property-page.md) ,

- La propiedad **directorios de biblioteca adicionales** en las **propiedades de configuración > enlazador >** página de propiedades general,

- La propiedad **dependencias adicionales** de las **propiedades de configuración > enlazador >** página de propiedades entrada.

## <a name="other-common-issues"></a>Otros problemas comunes

### <a name="path-or-filename-issues"></a>Problemas de ruta de acceso o nombre de archivo

Este error puede producirse si el nombre de archivo o la ruta de acceso de la biblioteca especificados para el vinculador no son correctos. O bien, cuando la ruta de acceso tiene una especificación de unidad no válida. Busque problemas en la línea de comandos o en cualquier [#pragma Comentario (lib, "LIBRARY_NAME")](../../preprocessor/comment-c-cpp.md) . Compruebe la ortografía y la extensión de archivo y compruebe que el archivo existe en la ubicación especificada.

### <a name="parallel-build-synchronization"></a>Sincronización de compilaciones paralelas

Si usa una opción de compilación en paralelo, es posible que Visual Studio haya bloqueado el archivo en otro subproceso. Para corregir este problema, compruebe que el mismo objeto de código o la misma biblioteca no está integrado en varios proyectos. Use las dependencias de compilación o las referencias de proyecto para seleccionar archivos binarios compilados en el proyecto.

### <a name="additional-dependencies-specified-in-the-ide"></a>Dependencias adicionales especificadas en el IDE

Al especificar bibliotecas individuales en la propiedad **dependencias adicionales** directamente, use espacios para separar los nombres de biblioteca. No use comas ni signos de punto y coma. Si usa el elemento de menú **Editar** para abrir el cuadro de diálogo **dependencias adicionales** , use nuevas líneas para separar los nombres, no comas, puntos y comas o espacios. También puede usar nuevas líneas al especificar rutas de acceso de biblioteca en los cuadros de diálogo **directorios de biblioteca** y **directorios de biblioteca adicionales** .

### <a name="paths-that-are-too-long"></a>Rutas de acceso demasiado largas

Es posible que vea este error cuando la ruta de acceso del *nombre de archivo* se expande a más de 260 caracteres. Si es necesario, reorganice la estructura de directorios o acorte la carpeta y los nombres de archivo para acortar las rutas de acceso.

### <a name="files-that-are-too-large"></a>Archivos demasiado grandes

Este error puede producirse porque el archivo es demasiado grande. Los archivos de bibliotecas o de objetos con un tamaño superior a un Gigabyte pueden causar problemas en el enlazador de 32 bits. Una posible solución para este problema es usar el conjunto de herramientas de 64 bits. Para obtener más información sobre cómo usar el conjunto de herramientas de 64 bits en la línea de comandos, vea [Cómo: habilitar un conjunto de C++ herramientas visual de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Para obtener información sobre cómo usar el conjunto de herramientas de 64 bits en el IDE, vea [usar MSBuild con el compilador y las herramientas de 64 bits](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project). Consulte también esta Stack Overflow post: [Cómo hacer que Visual Studio use la cadena de herramientas AMD64 nativa](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

### <a name="incorrect-file-permissions"></a>Permisos de archivo incorrectos

Este error puede producirse si no tiene suficientes permisos de archivo para tener acceso al *nombre*de archivo. Puede ocurrir si utiliza una cuenta de usuario normal para tener acceso a los archivos de biblioteca en directorios del sistema protegidos. O bien, si utiliza archivos copiados de otros usuarios que todavía tienen su conjunto de permisos original. Para corregir este problema, mueva el archivo a un directorio de proyecto grabable. Si el archivo que se ha descargado tiene permisos inaccesibles, ejecute el comando takeown. exe en una ventana de comandos de administrador para tomar posesión del archivo.

### <a name="insufficient-disk-space"></a>Espacio de disco insuficiente

El error puede producirse cuando no hay suficiente espacio en disco. El enlazador usa archivos temporales en varios casos. Aunque tenga suficiente espacio en disco, un vínculo grande puede agotar o fragmentar el espacio disponible en disco. Considere la posibilidad de usar la opción [/OPT (optimizaciones)](../../build/reference/opt-optimizations.md) ; la eliminación transitiva de COMDAT Lee todos los archivos objeto varias veces.

### <a name="problems-in-the-tmp-environment-variable"></a>Problemas en la variable de entorno TMP

Si el *nombre de archivo* se denomina lnk*nnn*, es un nombre de archivo generado por el enlazador para un archivo temporal. Es posible que el directorio especificado en la variable de entorno TMP no exista. O bien, se puede especificar más de un directorio para la variable de entorno TMP. Solo se debe especificar una ruta de acceso de directorio para la variable de entorno TMP.

## <a name="help-my-issue-isnt-listed-here"></a>Ayuda, mi problema no aparece aquí.

Si no se aplica ninguno de los problemas enumerados aquí, puede usar las herramientas de comentarios de Visual Studio para obtener ayuda. En el IDE, vaya a la barra de menús y elija **ayuda > enviar comentarios > notificar un problema**. O bien, envíe una sugerencia mediante la **ayuda > enviar comentarios > enviar una sugerencia**. También puede usar el sitio web de C++ la [comunidad de desarrolladores](https://developercommunity.visualstudio.com/spaces/62/index.html)de Visual Studio). Úselo para buscar respuestas a preguntas y solicitar ayuda. Para obtener más información, vea [Cómo notificar un problema con el C++ conjunto de herramientas visual o la documentación](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)de.

Si ha descubierto un nuevo modo de corregir este problema que deberíamos agregar a este artículo, háganoslo saber. Puede enviarnos sus comentarios mediante el botón siguiente para **esta página**. Úselo para crear un nuevo problema en nuestro [ C++ repositorio de github de documentación](https://github.com/MicrosoftDocs/cpp-docs/issues). Gracias
