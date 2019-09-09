---
title: Error de las herramientas del vinculador LNK1104
ms.date: 09/06/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: f3effd9054954a90f69c5b18d8f099e6d705d9a3
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808839"
---
# <a name="linker-tools-error-lnk1104"></a>Error de las herramientas del vinculador LNK1104

> no se puede abrir el archivo '*nombreDeArchivo*'

El enlazador no pudo abrir el archivo especificado. Las causas más comunes de este problema son que el archivo está en uso o bloqueado por otro proceso. También es posible que el archivo no exista o no se encuentre en uno de los directorios que busca el enlazador. O bien, puede que no tenga permisos suficientes para obtener acceso al archivo. Con menos frecuencia, es posible que se haya quedado sin espacio en disco, que el archivo sea demasiado grande o que la ruta de acceso al archivo sea demasiado larga.

## <a name="possible-causes-and-solutions"></a>Posibles causas y soluciones

Este error puede producirse cuando el vinculador intenta abrir un archivo para leerlo o para escritura. Para reducir las causas posibles, compruebe primero qué tipo de archivo es. A continuación, use las secciones siguientes para ayudar a identificar y corregir el problema específico.

### <a name="cant-open-your-app-or-its-pdb-file"></a>No se puede abrir la aplicación ni su archivo. pdb

Si el nombre de archivo es el ejecutable que se va a compilar el proyecto, o un archivo. pdb asociado, la causa más común es que la aplicación ya se está ejecutando cuando se intenta volver a generar o se carga en un depurador. Para corregir este problema, detenga el programa y descárguelo del depurador antes de compilarlo de nuevo. Si la aplicación está abierta en otro programa, como un editor de recursos, ciérrela. En casos extremos, puede que tenga que usar el administrador de tareas para finalizar el proceso o detener y reiniciar Visual Studio.

Los programas antivirus suelen bloquear temporalmente el acceso a los archivos recién creados, especialmente a los archivos ejecutables. exe y. dll. Para solucionar este problema, pruebe a excluir los directorios de compilación del proyecto del detector de virus.

### <a name="cant-open-a-microsoft-library-file"></a>No se puede abrir un archivo de biblioteca de Microsoft

Si el archivo que no se puede abrir es uno de los archivos de la biblioteca estándar que proporciona Microsoft, como Kernel32. lib, puede tener un error de configuración del proyecto o un error de instalación. Compruebe que se ha instalado el Windows SDK y, si el proyecto requiere otras bibliotecas de Microsoft, como MFC, asegúrese de que el instalador de Visual Studio también instaló los componentes de MFC. Puede volver a ejecutar el instalador para agregar componentes opcionales en cualquier momento. Para obtener más información, vea [modificar Visual Studio](/visualstudio/install/modify-visual-studio). Use la pestaña componentes individuales del instalador para elegir bibliotecas y SDK específicos.

No hay ninguna biblioteca Spectre para los componentes o aplicaciones universales de Windows (UWP). Si el informe de errores menciona el archivo *vccorlib. lib* , es posible que haya habilitado [/Qspectre](../../build/reference/qspectre.md) en un proyecto de UWP. Deshabilite la opción del compilador **/Qspectre** para corregir este problema. En Visual Studio, cambie la propiedad **Mitigation de Spectre** , que se encuentra en la página**generación de código** **C yC++**  > del cuadro de diálogo páginas de **propiedades** del proyecto.

Si va a compilar un proyecto creado con una versión anterior de Visual Studio, es posible que el conjunto de herramientas de la plataforma y las bibliotecas de esa versión no estén instaladas. Si el mensaje de error se produce para un nombre de biblioteca con versión, como msvcr100. lib, es probable que esta sea la causa. Para corregir este problema, tiene dos opciones: puede actualizar el proyecto para usar el conjunto de herramientas de la plataforma actual que ha instalado, o puede instalar el conjunto de herramientas anterior y compilar el proyecto sin cambios. Para obtener más información, vea [actualizar proyectos de versiones anteriores de Visual C++ ](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) y [usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos](../../porting/use-native-multi-targeting.md).

Si ve este error al compilar para una nueva plataforma o configuración de destino, es posible que las bibliotecas de la configuración del proyecto o el conjunto de herramientas de la plataforma no estén instaladas. Compruebe que el **conjunto de herramientas** de la plataforma y la **versión de Windows SDK** especificadas en la [Página de propiedades general](../../build/reference/general-property-page-project.md) del proyecto están instaladas y compruebe que las bibliotecas necesarias están disponibles en los **directorios de biblioteca** especificados en la [Página de propiedades de los directorios de VC + +](../../build/reference/vcpp-directories-property-page.md) de las opciones de configuración. Hay configuraciones independientes para las configuraciones de depuración y de venta directa, así como las configuraciones de 32 y 64 bits, por lo que si una compilación funciona pero otra causa un error, asegúrese de que la configuración sea correcta y de que se instalen las herramientas y bibliotecas necesarias para cada configuración que se compila.

Si usa el IDE de Visual Studio para compilar un proyecto que se copió desde otro equipo, las ubicaciones de instalación de las bibliotecas pueden ser diferentes. Compruebe la propiedad **directorios de biblioteca** en la página de [propiedades directorios de VC + +](../../build/reference/vcpp-directories-property-page.md) del proyecto y actualícelo si es necesario. Para ver y editar las rutas de acceso de biblioteca actuales establecidas en el IDE, elija el control desplegable de la propiedad **directorios de biblioteca** y elija **Editar**. En la sección **valor evaluado** del cuadro de diálogo **directorios de biblioteca** se muestran las rutas de acceso actuales que se buscan en los archivos de biblioteca.

Este error también puede producirse si la ruta de acceso al Windows SDK no está actualizada. Si ha instalado una versión de la Windows SDK que es más reciente que la versión de Visual Studio, asegúrese de que las rutas de acceso especificadas en la [Página de propiedades directorios de VC + +](../../build/reference/vcpp-directories-property-page.md) se han actualizado para que coincidan con el nuevo SDK. Si usa el Símbolo del sistema para desarrolladores, asegúrese de que el archivo por lotes que inicializa las variables de entorno se actualiza para las nuevas rutas de acceso del SDK. Este problema se puede evitar mediante el instalador de Visual Studio para instalar los SDK actualizados.

### <a name="cannot-open-a-third-party-library-file"></a>No se puede abrir un archivo de biblioteca de otro fabricante

Hay varias causas comunes para este problema:

- Es posible que la ruta de acceso al archivo de biblioteca no sea correcta o que no se haya especificado en el enlazador.

- Es posible que haya instalado una versión de 32 bits de la biblioteca, pero está compilando para 64 bits, o viceversa.

- La biblioteca puede tener dependencias en otras bibliotecas que no están instaladas.

Para corregir un problema de ruta de acceso, compruebe que la variable de entorno LIB esté establecida y que contenga todos los directorios de las bibliotecas que usa, para cada configuración que cree. En el IDE, la variable LIB se establece mediante la propiedad **directorios de biblioteca** en la página de [propiedades directorios de VC + +](../../build/reference/vcpp-directories-property-page.md). Asegúrese de que todos los directorios que contienen las bibliotecas que necesita aparecen aquí, para cada configuración que cree.

Si necesita proporcionar un directorio de biblioteca que invalide un directorio de biblioteca estándar, puede usar la opción [/LIBPATH](../../build/reference/libpath-additional-libpath.md) en la línea de comandos o en el IDE, puede usar la propiedad **directorios de biblioteca adicionales** en las **propiedades de configuración. > Enlazador >** página de propiedades general del proyecto.

Asegúrese de que ha instalado todas las versiones de la biblioteca que necesita para las configuraciones que cree. Considere la posibilidad de usar la utilidad de administración de paquetes [vcpkg](../../vcpkg.md) para automatizar la instalación y la configuración de muchas bibliotecas comunes. Cuando sea posible, es mejor crear sus propias copias de bibliotecas de terceros, por lo que asegúrese de tener todas las dependencias locales que las bibliotecas requieran y se compilan para la misma configuración que el proyecto.

### <a name="cannot-open-a-file-built-by-your-project"></a>No se puede abrir un archivo compilado por el proyecto

Es posible que vea este error si el *nombre* de archivo está compilado en la solución, pero aún no existe cuando el enlazador intenta tener acceso a él. Esto puede ocurrir cuando un proyecto depende de otro proyecto, pero los proyectos no se compilan en el orden correcto. Para corregir este problema, asegúrese de que las referencias del proyecto se establecen en el proyecto que utiliza el archivo para que el archivo que falta se compile antes de que sea necesario. Para obtener más información, vea [Agregar referencias en proyectos C++ de Visual Studio](../../build/adding-references-in-visual-cpp-projects.md) y [administrar referencias en un proyecto](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>No se puede abrir el archivo\\' C: Program. obj '

Si ve este error, o un error similar relacionado con un archivo. obj inesperado en la raíz de la unidad, el problema es casi seguro una ruta de acceso de biblioteca que no está incluida entre comillas dobles.

Para corregir este problema en las compilaciones desde la línea de comandos, compruebe los parámetros de la opción [/LIBPATH](../../build/reference/libpath-additional-libpath.md) , las rutas de acceso especificadas en la variable de entorno lib y las rutas de acceso especificadas en la línea de comandos, y asegúrese de usar comillas dobles alrededor de las rutas de acceso que incluyan espacios.

Para corregir este problema en el IDE, Compruebe la propiedad **directorios de biblioteca** en las propiedades de configuración > Página de propiedades directorios de [VC + +](../../build/reference/vcpp-directories-property-page.md) , la propiedad directorios de **biblioteca adicionales** en las **propiedades de configuración > enlazador. >** Página de propiedades general y la propiedad **dependencias adicionales** en las **propiedades de configuración > enlazador >** página de propiedades entrada del proyecto. Asegúrese de que todas las rutas de acceso de directorio que contienen las bibliotecas que necesita se incluyen entre comillas dobles si es necesario.

### <a name="other-common-issues"></a>Otros problemas comunes

Este error puede producirse si el nombre de archivo o la ruta de acceso de la biblioteca especificados para el vinculador en la línea de comandos o en un [#pragma Comentario (lib, "LIBRARY_NAME")](../../preprocessor/comment-c-cpp.md) es incorrecto o la ruta de acceso tiene una especificación de unidad no válida. Compruebe la ortografía y la extensión de archivo y compruebe que el archivo existe en la ubicación especificada.

Puede que otro programa tenga el archivo abierto y que el enlazador no puede escribir en él. Los programas antivirus suelen bloquear temporalmente el acceso a los archivos recién creados. Para solucionar este problema, pruebe a excluir los directorios de compilación del proyecto del detector de virus.

Si usa una opción de compilación en paralelo, es posible que Visual Studio haya bloqueado el archivo en otro subproceso. Para corregir este problema, compruebe que no compila el mismo objeto de código o la misma biblioteca en varios proyectos, y que se utilizan dependencias de compilación o referencias de proyecto para seleccionar archivos binarios compilados en el proyecto.

Al especificar bibliotecas individuales en la propiedad **dependencias adicionales** directamente, use espacios para separar los nombres de biblioteca, no comas ni puntos y comas. Si usa el elemento de menú **Editar** para abrir el cuadro de diálogo **dependencias adicionales** , use nuevas líneas para separar los nombres, no comas, puntos y comas o espacios. También puede usar nuevas líneas al especificar rutas de acceso de biblioteca en los cuadros de diálogo **directorios de biblioteca** y **directorios de biblioteca adicionales** .

Es posible que vea este error cuando la ruta de acceso del *nombre de archivo* se expande a más de 260 caracteres. Cambie los nombres o reorganice la estructura de directorios si es necesario para acortar las rutas de acceso a los archivos necesarios.

Este error puede producirse porque el archivo es demasiado grande. Los archivos de bibliotecas o de objetos con un tamaño superior a un Gigabyte pueden causar problemas en el enlazador de 32 bits. Una posible solución para este problema es usar el conjunto de herramientas de 64 bits. Para obtener más información sobre cómo hacerlo en la línea de comandos, consulte [cómo: Habilite un conjunto de herramientas visual C++ de 64 bits en la](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)línea de comandos. Para obtener información sobre cómo hacer esto en el IDE, vea [usar MSBuild con el compilador y las herramientas de 64](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) y este Stack Overflow post: [Cómo hacer que Visual Studio use la cadena de herramientas AMD64 nativa](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

Este error puede producirse si no tiene suficientes permisos de archivo para tener acceso al *nombre*de archivo. Esto puede ocurrir si se usa una cuenta de usuario normal y se intenta tener acceso a los archivos de biblioteca en directorios del sistema protegidos, o se utilizan archivos copiados de otros usuarios que tienen su conjunto de permisos original. Para corregir este problema, mueva el archivo a un directorio de proyecto grabable. Si el archivo se encuentra en un directorio grabable pero tiene permisos inaccesibles, puede utilizar un símbolo del sistema de administrador y ejecutar el comando takeown. exe para tomar posesión del archivo.

El error puede producirse cuando no hay suficiente espacio en disco. El enlazador usa archivos temporales en varios casos. Incluso si tiene suficiente espacio en disco, un vínculo muy grande puede agotar o fragmentar el espacio disponible en disco. Considere la posibilidad de usar la opción [/OPT (optimizaciones)](../../build/reference/opt-optimizations.md) ; la eliminación transitiva de COMDAT Lee todos los archivos objeto varias veces.

Si el *nombre* de archivo se denomina lnk*nnn*, que es un nombre de archivo generado por el enlazador para un archivo temporal, es posible que el directorio especificado en la variable de entorno TMP no exista o que se especifique más de un directorio para la variable de entorno TMP. Solo se debe especificar una ruta de acceso de directorio para la variable de entorno TMP.
