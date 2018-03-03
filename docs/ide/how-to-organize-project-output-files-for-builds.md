---
title: "Cómo: organizar archivos de salida del proyecto para la compilación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 648321c41fe02541eeb746bae24236c40dc5325e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Cómo: Organizar archivos de resultados de proyectos para la compilación
En este tema se describe procedimientos recomendados para organizar los archivos de salida del proyecto. Compilar pueden producirse errores al configurar archivos de salida del proyecto de forma incorrecta. Este tema también describen las ventajas y desventajas de cada alternativa para organizar los archivos de salida del proyecto.  
  
## <a name="referencing-clr-assemblies"></a>Hacer referencia a ensamblados CLR  
  
#### <a name="to-reference-assemblies-with-using"></a>A los ensamblados de referencia con #using  
  
1.  Se puede hacer referencia a un ensamblado directamente desde el código mediante el uso de la # directiva using, como `#using <System.Data.dll>`. Para obtener más información, consulte [#using (directiva)](../preprocessor/hash-using-directive-cpp.md).  
  
     El archivo especificado puede ser un archivo .dll, .exe, .netmodule o .obj, siempre y cuando sea en MSIL. El componente que se hace referencia se puede crear en cualquier lenguaje. Con esta opción, tendrá acceso a Intellisense desde que se van a extraer los metadatos desde el código MSIL. El archivo en cuestión debe estar en la ruta de acceso para el proyecto; en caso contrario, no se compilará el proyecto y Intellisense no estará disponible. Una manera fácil de determinar si el archivo está en la ruta de acceso es haga doble clic en el # línea using y elegir la **documento abierto** comando. Se le notificará si no se encuentra el archivo.  
  
     Si no desea colocar la ruta de acceso completa al archivo, puede usar el **/AI** opción del compilador para editar la ruta de acceso de búsqueda para #using referencias. Para obtener más información, consulte [/AI (Especificar directorios de metadatos)](../build/reference/ai-specify-metadata-directories.md).  
  
#### <a name="to-reference-assemblies-with-fu"></a>Para hacer referencia a ensamblados con /FU  
  
1.  En lugar de hacer referencia a un ensamblado directamente desde un archivo de código, tal y como se ha descrito anteriormente, puede usar el **/FU** opción del compilador. La ventaja de este método es que no tiene que agregar una #using instrucción a todos los archivos que se hace referencia a un ensamblado dado.  
  
     Para establecer esta opción, abra el **páginas de propiedades** para el proyecto. Expanda el **propiedades de configuración** nodo y, a continuación, expanda el **C/C++** nodo y seleccione **avanzadas**. Agregue los ensamblados deseados junto a **Force #using**. Para obtener más información, consulte [/FU (Dar nombre al archivo #using forzado)](../build/reference/fu-name-forced-hash-using-file.md).  
  
#### <a name="to-reference-assemblies-with-add-new-reference"></a>Para hacer referencia a ensamblados con Agregar nueva referencia  
  
1.  Se trata de la manera más fácil de usar ensamblados CLR. En primer lugar, asegúrese de que el proyecto se compila con la **/CLR** opción del compilador. A continuación, haga clic el proyecto desde el **el Explorador de soluciones** y seleccione **agregar**, **referencias**. El **páginas de propiedades** aparecerá el cuadro de diálogo.  
  
2.  Desde el **páginas de propiedades** cuadro de diálogo, seleccione **agregar nueva referencia**. Aparecerá un cuadro de diálogo enumerar todos los .NET, COM y otros ensamblados disponibles en el proyecto actual. Seleccione el ensamblado que desee y haga clic en **Aceptar**.  
  
     Una vez que se establece una referencia de proyecto, las dependencias correspondientes se administran automáticamente. Además, puesto que los metadatos de forman parte de un ensamblado, es necesario para agregar un archivo de encabezado o el prototipo de los elementos que se utilizan desde ensamblados administrados.  
  
## <a name="referencing-native-dlls-or-static-libraries"></a>Hacer referencia a archivos DLL nativos o bibliotecas estáticas  
  
#### <a name="to-reference-native-dlls-or-static-libraries"></a>Hacer referencia a archivos DLL nativos o bibliotecas estáticas  
  
1.  Hacer referencia al archivo de encabezado adecuado en el código utilizando el #include (directiva). El archivo de encabezado debe estar en la ruta de acceso de inclusión o parte del proyecto actual. Para obtener más información, consulte [#include (directiva) (C/C ++)](../preprocessor/hash-include-directive-c-cpp.md).  
  
2.  También puede establecer dependencias del proyecto. Al establecer las dependencias de proyecto garantiza dos cosas. En primer lugar, se asegura de que los proyectos se generan en el orden correcto para que un proyecto siempre puedan encontrar los archivos dependientes que necesita. En segundo lugar, agrega implícitamente directorio de salida del proyecto dependiente a la ruta de acceso para que los archivos se puedan encontrar fácilmente en tiempo de vinculación.  
  
3.  Para implementar la aplicación, debe colocar el archivo DLL en un lugar adecuado. Esto puede ser uno de los siguientes:  
  
    1.  La misma ruta que el archivo ejecutable.  
  
    2.  En cualquier parte de la ruta de acceso del sistema (la **ruta de acceso** variable de entorno).  
  
    3.  En el ensamblado en paralelo. Para obtener más información, consulte [creación de ensamblados de C o C++-paralelo](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="working-with-multiple-projects"></a>Trabajar con varios proyectos  
 De forma predeterminada, proyectos se generan de forma que todos los archivos de salida se crean en un subdirectorio del directorio del proyecto. El directorio se denomina en función de la configuración de compilación (por ejemplo, depuración o lanzamiento). En el orden de los proyectos de mismo nivel hacer referencia a entre sí, cada proyecto debe agregar explícitamente los directorios de salida de proyecto para su ruta de acceso en orden para crear un vínculo para tener éxito. Esto se hace automáticamente al establecer las dependencias del proyecto. Sin embargo, si no utiliza dependencias, debe controlar esto cuidadosamente porque pueden ser muy difíciles administrar compilaciones. Por ejemplo, cuando un proyecto tiene configuraciones Debug y Release, e incluye una biblioteca externa de un proyecto relacionado, debe usar un archivo de biblioteca diferente dependiendo de qué configuración se está generando. Por lo tanto, codificar de forma rígida estas rutas de acceso puede ser complicada.  
  
 Todos los archivos de salida esenciales (por ejemplo, los archivos ejecutables, archivos de vinculador incremental y archivos PDB) se copian en un directorio de soluciones común. Por lo tanto, cuando se trabaja con una solución que contiene un número de proyectos de C++ con configuraciones equivalentes, todos los archivos de salida se centralizan para simplificar la vinculación y la implementación. Puede estar seguro de que las aplicaciones y bibliotecas funcionará según lo esperado si mantiene juntos estos archivos (desde que se garantiza que los archivos estén en la ruta de acceso).  
  
 La ubicación de archivos de salida puede ser un problema importante cuando se implementa en un entorno de producción. Durante la ejecución de proyectos en el IDE, las rutas de acceso a las bibliotecas incluidas no son necesariamente el mismo que en el entorno de producción. Por ejemplo, si tiene `#using "../../lib/debug/mylib.dll"` en el código pero implementa mylib.dll en una posición relativa diferente, se producirá un error de la aplicación en tiempo de ejecución. Para evitar esto, debe evitar el uso de rutas de acceso relativas en # instrucciones include en el código. Es mejor asegurarse de que los archivos necesarios se encuentran en la ruta de acceso de compilación del proyecto y del mismo modo asegurarse de que los archivos de producción correspondientes se colocan correctamente.  
  
#### <a name="how-to-specify-where-output-files-go"></a>Cómo especificar dónde van los archivos de salida  
  
1.  Salida de la ubicación del proyecto de configuración puede encontrarse en el proyecto **páginas de propiedades**. Expanda el nodo junto a **propiedades de configuración** y seleccione **General**. La ubicación de salida se especifica junto a **directorio de salida**. Para obtener más información, consulte [página de propiedades General (proyecto)](../ide/general-property-page-project.md).  
  
## <a name="see-also"></a>Vea también  
 [Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)