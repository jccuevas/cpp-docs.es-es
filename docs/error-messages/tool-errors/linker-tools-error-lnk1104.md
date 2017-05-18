---
title: Las herramientas del vinculador LNK1104 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: c6121f598bc2913b65fe781b07bcc27e6b55375b
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---
# <a name="linker-tools-error-lnk1104"></a>Error de las herramientas del vinculador LNK1104
no se puede abrir el archivo '*filename*'  
  
El vinculador no pudo abrir el archivo especificado.  
  
## <a name="possible-causes-and-solutions"></a>Posibles causas y soluciones
  
Este error puede producirse cuando el vinculador intenta abrir un archivo para lectura o escritura. Las causas más comunes de este problema son que el archivo no existe, no se encuentra en uno de los directorios el vinculador busca, o está en uso y bloqueado por otro proceso. Menos frecuente, puede haberse quedado sin espacio en disco, el archivo puede ser demasiado grande, la ruta de acceso al archivo puede ser demasiado largo o puede que no tenga permiso para tener acceso al archivo.  

Compruebe si alguno de estos problemas comunes:  

-   Ya se está ejecutando la aplicación al intentar volver a compilarlo. Si el archivo que no se puede abrir el archivo ejecutable o un archivo de depuración, como un archivo .pdb, esto es una causa común. Para corregir este problema, detenga el programa y descargarlo desde el depurador antes de crear de nuevo.  
  
-   El archivo *filename* compilados por su solución, pero que aún no existe cuando el vinculador intenta obtener acceso a él. Esto puede ocurrir cuando un proyecto depende de otro proyecto para generar este archivo, pero no se compilan los proyectos en el orden correcto. Para corregir este problema, asegúrese de que las referencias del proyecto se establecen en el proyecto que utiliza el archivo para que el archivo que falta se genera antes de que sea necesario. Para obtener más información, consulte [agregar referencias en proyectos de Visual C++](../../ide/adding-references-in-visual-cpp-projects.md) y [administrar referencias en un proyecto](/visualstudio/ide/managing-references-in-a-project).  
  
-   El nombre de archivo o ruta de acceso especificada en la línea de comandos o en una directiva de lib #pragma es incorrecta o la ruta de acceso tiene una especificación de unidad no válida. Compruebe la ortografía y que el archivo existe en la ubicación especificada.  
  
-   Si está usando el IDE de Visual Studio para compilar un proyecto que se copió desde otro equipo, las ubicaciones de instalación para las bibliotecas pueden variar. Compruebe la propiedad directorios de bibliotecas en el [página de propiedades de directorios de VC ++](../../ide/vcpp-directories-property-page.md) y actualícelo si es necesario. Para ver y editar las rutas de acceso de biblioteca actuales establecidas en el IDE, elija el control de lista desplegable para la propiedad de directorios de bibliotecas y elija **editar**. El **evalúa valor** sección del cuadro de diálogo directorios de bibliotecas enumeran las rutas de acceso actuales buscados archivos de biblioteca.  
  
-   Si va a compilar un proyecto que se creó con una versión anterior de Visual Studio, el conjunto de herramientas de plataforma y las bibliotecas de esa versión pueden no no ser instaladas. Para corregir este problema, tiene dos opciones: puede actualizar el proyecto para utilizar el conjunto de herramientas de plataforma actual ha instalado, o puede instalar el conjunto de herramientas anterior y compile el proyecto sin cambios. Para obtener más información, consulte [actualizar proyectos desde versiones anteriores de Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) y [utilizar nativa con múltiples versiones de Visual Studio para compilar proyectos antiguos](../../porting/use-native-multi-targeting.md).
  
-   No se instalan las bibliotecas para la configuración del proyecto actual o el conjunto de herramientas de plataforma. Compruebe que el conjunto de herramientas de plataforma y el SDK de Windows especifican en el [página de propiedades General](../../ide/general-property-page-project.md) están instalados para el proyecto y compruebe que las bibliotecas necesarias están disponibles en la biblioteca de los directorios especificados en la [página de propiedades de directorios de VC ++](../../ide/vcpp-directories-property-page.md) para las opciones de configuración. Hay opciones de configuración independientes para configuraciones Debug y comercial, por lo que si uno funcionan las compilaciones, pero el otro produce un error, asegúrese de que la configuración es correcta y las herramientas necesarias y las bibliotecas se instalan para ambas configuraciones.  
  
-   La ruta de acceso para el SDK de Windows está anticuada. Si ha instalado una versión del SDK de Windows más reciente que la versión de Visual Studio, asegúrese de que las rutas de acceso especifican en el [página de propiedades de directorios de VC ++](../../ide/vcpp-directories-property-page.md) se actualizan para que coincida con el nuevo SDK. Si usa el símbolo del sistema para desarrolladores, asegúrese de que el archivo por lotes que inicializa las variables de entorno se actualiza para las nuevas rutas SDK.  
  
-   Puede que otro programa tenga el archivo abierto y que el enlazador no puede escribir en él. Los programas antivirus a menudo bloquean temporalmente el acceso a los archivos recién creados. Para corregir este problema, pruebe excluyendo los directorios de compilación de proyecto desde el programa antivirus.  
  
-   Si está utilizando una opción de compilación paralela, es posible que Visual Studio ha bloqueado el archivo en otro subproceso. Para corregir este problema, compruebe que no genere el mismo objeto de código o la biblioteca en varios proyectos y usar las dependencias de compilación ni ninguna referencia de proyecto para recoger archivos binarios generados en el proyecto.  
  
-   Tiene una variable de entorno LIB incorrecta. En las compilaciones de línea de comandos, compruebe que la variable de entorno LIB se establece y contiene todos los directorios para las bibliotecas que utiliza. En el IDE, la variable LIB es establecida por la propiedad de directorios de bibliotecas en el [página de propiedades de directorios de VC ++](../../ide/vcpp-directories-property-page.md). Asegúrese de que todos los directorios que contienen las bibliotecas que necesita aparecen aquí. Si tiene que proporcionar un directorio de la biblioteca que invalida un directorio de la biblioteca estándar, puede usar el [/libpath](../../build/reference/libpath-additional-libpath.md)) opción en la línea de comandos o la propiedad de directorios de bibliotecas adicionales en la página de propiedades del vinculador para el proyecto.  
  
-   Al especificar bibliotecas individuales en el cuadro de diálogo páginas de propiedades del proyecto, nombres de las bibliotecas deben estar separados por espacios, no por comas.  
  
-   La ruta de acceso *filename* se expande a más de 260 caracteres. Cambiar los nombres o reorganizar la estructura de directorios si es necesario para acortar las rutas de acceso a los archivos necesarios.  
  
-   El archivo es demasiado grande. Objeto o bibliotecas de archivos de más de un gigabyte de tamaño puede causar problemas para que el vinculador de 32 bits. Una posible solución para este problema consiste en utilizar el conjunto de herramientas de 64 bits. Para obtener más información sobre cómo hacer esto en la línea de comandos, consulte [Cómo: habilitar un 64-Bit Visual C++ Toolset en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Para obtener información sobre cómo hacer esto en el IDE, vea [usar MSBuild con el compilador de 64 bits y herramientas](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) y esta entrada de desbordamiento de la pila: [cómo hacer que Visual Studio utiliza la cadena de herramientas nativo amd64](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).  
  
-   Tener permisos de archivo insuficientes para tener acceso a *filename*. Esto puede ocurrir si el acceso a los archivos de biblioteca en directorios protegidos del sistema, o usar los archivos copiados de otros usuarios que tengan los permisos originales establecido. Para corregir este problema, mueva el archivo a un directorio de proyecto grabable. Si el archivo está en un directorio de escritura pero tiene permisos inaccesibles, puede usar un símbolo del sistema de administrador y ejecute el comando de takeown.exe tomar posesión del archivo.  
  
-   No tiene suficiente espacio en disco. El enlazador usa archivos temporales en varios casos. Aunque tenga suficiente espacio en disco, un vínculo muy grande puede disminuir o fragmentar el espacio en disco disponible. Considere el uso de la [especificación /OPT (optimizaciones)](../../build/reference/opt-optimizations.md) opción; realizar lecturas de eliminación de comdat transitiva todos los archivos objeto varias veces.  
  
-   Si el *filename* se denomina LNK*n*, que es un nombre de archivo generado por el vinculador para un archivo temporal, puede que no exista el directorio especificado en la variable de entorno TMP, o se puede especificar más de un directorio para la variable de entorno TMP. Debe especificarse solo una ruta de acceso para la variable de entorno TMP.  
  
-   Si el mensaje de error se produce para un nombre de biblioteca, y se portó recientemente el archivo .mak de un sistema de desarrollo de Microsoft Visual C++ anterior, es posible que la biblioteca ya no sea válida. Asegúrese de que el nombre de la biblioteca es correcto y que sigue existiendo en la ubicación especificada, o actualizar la ruta de acceso LIB para que apunte a la nueva ubicación.  

