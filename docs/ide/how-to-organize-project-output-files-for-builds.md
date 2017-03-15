---
title: "C&#243;mo: Organizar archivos de resultados de proyectos para la compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de salida, organizar"
  - "Visual C++, archivos de salida"
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# C&#243;mo: Organizar archivos de resultados de proyectos para la compilaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se describen los procedimientos recomendados para organizar los archivos de resultado del proyecto.  Pueden aparecer errores de compilación cuando los archivos de resultado del proyecto se preparan incorrectamente.  Este tema también esquematiza las ventajas y desventajas de cada alternativa para organizar los archivos de resultado del proyecto.  
  
## Hacer referencia a ensamblados CLR  
  
#### Para hacer referencia a ensamblados con \#using  
  
1.  Puede hacer referencia a un ensamblado directamente desde el código utilizando la directiva \#using, como en `#using <System.Data.dll>`.  Para obtener más información, vea [\#using \(Directiva\)](../preprocessor/hash-using-directive-cpp.md).  
  
     El archivo especificado puede ser .dll, .exe, .netmodule u .obj, siempre y cuando sea en MSIL.  El componente al que se hace referencia puede compilarse en cualquier lenguaje.  Con esta opción tendrá acceso a Intellisense, puesto que los metadatos se extraerán del MSIL.  El archivo en cuestión debe estar en la ruta de acceso para el proyecto; de lo contrario, el proyecto no se compilará y no estará disponible Intellisense.  Una forma fácil de determinar si el archivo está en la ruta de acceso es hacer clic con el botón secundario del mouse en la línea \#using y elegir el comando **Abrir documento**.  Se le notificará si no se encuentra el archivo.  
  
     Si no desea poner la ruta completa de acceso al archivo, puede utilizar la opción **\/AI** del compilador para editar la ruta de búsqueda de referencias \#using.  Para obtener más información, vea [\/AI \(Especificar directorios de metadatos\)](../build/reference/ai-specify-metadata-directories.md).  
  
#### Para hacer referencia a ensamblados con \/FU  
  
1.  En lugar de hacer referencia directamente a un ensamblado desde un archivo de código, como se describió anteriormente, puede utilizar la opción **\/FU** del compilador.  La ventana de este método es que no necesitará agregar una instrucción \#using separada a cada archivo que haga referencia a un ensamblado dado.  
  
     Para establecer esta opción, abra las **Páginas de propiedades** del proyecto.  Expanda el nodo **Propiedades de configuración**, expanda el nodo **C\/C\+\+** y seleccione **Avanzadas**.  Agregue los ensamblados deseados junto **Forzar \#using**.  Para obtener más información, vea [\/FU \(Asignar nombre al archivo \#using obligatorio\)](../build/reference/fu-name-forced-hash-using-file.md).  
  
#### Para hacer referencia a ensamblados con Agregar nueva referencia  
  
1.  Esta es la manera más fácil de utilizar los ensamblados CLR.  Primero, asegúrese de que el proyecto se compila con la opción del compilador **\/clr**.  A continuación, haga clic con el botón secundario del mouse en el proyecto en el **Explorador de soluciones** y seleccione **Agregar**, **Referencias**.  Aparecerá el cuadro de diálogo **Páginas de propiedades**.  
  
2.  En el cuadro de diálogo **Páginas de propiedades**, seleccione **Agregar nueva referencia**.  Aparecerá un cuadro de diálogo que muestra todos los ensamblados .NET, COM y otros disponibles en el proyecto actual.  Seleccione el ensamblado que desee y haga clic en **Aceptar**.  
  
     Cuando se establece una referencia de proyecto, las dependencias correspondientes se controlan automáticamente.  Además, puesto que los metadatos forman parte de un ensamblado, no es necesario agregar un archivo de encabezado ni crear prototipos de los elementos que se utilizan desde ensamblados administrados.  
  
## Hacer referencia a archivos DLL o bibliotecas estáticas nativas  
  
#### Para hacer referencia a archivos DLL o bibliotecas estáticas nativas  
  
1.  Haga referencia al archivo de encabezado adecuado en el código utilizando la directiva \#include.  El archivo de encabezado debe estar en la ruta de inclusión o formar parte del proyecto actual.  Para obtener más información, vea [\#include \(Directiva\)](../preprocessor/hash-include-directive-c-cpp.md).  
  
2.  También puede establecer dependencias de proyecto.  La configuración de dependencias de proyecto garantiza dos cosas.  Primero, garantiza que los proyectos se compilan en el orden correcto de modo que un proyecto siempre encuentre los archivos dependientes que necesite.  Segundo, agrega implícitamente el directorio de salida del proyecto dependiente a la ruta de acceso, para que los archivos se puedan encontrar con facilidad en tiempo de vinculación.  
  
3.  Para implementar la aplicación, deberá colocar el archivo DLL en un lugar adecuado.  Puede ser cualquiera de los siguientes:  
  
    1.  La misma ruta de acceso que el ejecutable.  
  
    2.  Cualquier punto de la ruta de acceso del sistema \(la variable de entorno **path**\).  
  
    3.  En el ensamblado en paralelo.  Para obtener más información, vea [Compilar ensamblados simultáneos de C\/C\+\+](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## Trabajar con varios proyectos  
 De forma predeterminada, los proyectos se compilan de modo que todos los archivos de salida se crean en un subdirectorio del directorio de proyecto.  El nombre del directorio depende de la configuración de compilación \(por ejemplo,  Depuración o Lanzamiento\).  Para que los proyectos relacionados se hagan referencia entre sí, cada uno de ellos debe agregar explícitamente a su ruta de acceso los directorios de salida del otro proyecto, para que la vinculación sea correcta.  Esto se hace automáticamente cuando se establecen las dependencias del proyecto.  Sin embargo, si no utiliza dependencias, debe controlar esto cuidadosamente porque las compilaciones pueden hacerse muy difíciles administrar.  Por ejemplo, cuando un proyecto tiene configuraciones de Depuración y Lanzamiento, e incluye una biblioteca externa de un proyecto relacionado, debe utilizar un archivo de biblioteca diferente en función de la configuración compilada.  Así, la inclusión en el código de estas rutas de acceso puede ser difícil.  
  
 Todos los archivos de salida esenciales \(como ejecutables, archivos de vinculador incremental y archivos PDB\) se copian en un directorio de soluciones común.  Así, cuando se trabaja con una solución que contiene varios proyectos C\+\+ con configuraciones equivalentes, todos los archivos de salida se centralizan para simplificar la vinculación y la implementación.  Sabrá con seguridad que las aplicaciones y bibliotecas funcionan según lo esperado si mantiene juntos estos archivos \(dado que se garantiza que los archivos están en la ruta de acceso\).  
  
 La ubicación de archivos de salida puede ser un problema importante cuando se implemente un entorno de producción.  Mientras se ejecutan proyectos en el IDE, las rutas de acceso a las bibliotecas incluidas no son necesariamente las mismas que en el entorno de producción.  Por ejemplo, si tiene `#using "../../lib/debug/mylib.dll"` en el código pero implementa mylib.dll en una posición relativa diferente, se producirá un error en la aplicación en el tiempo de ejecución.  Para evitarlo, es recomendable evitar el uso de rutas de acceso relativas en instrucciones \#include en el código.  Es mejor asegurarse de que los archivos necesarios se encuentran en la ruta de acceso de compilación del proyecto y, de forma similar, que los archivos de producción correspondientes están colocados correctamente.  
  
#### Cómo especificar dónde van los archivos de salida  
  
1.  La configuración de la ubicación de los resultados del proyecto se encuentra en las **Páginas de propiedades** del proyecto.  Expanda el nodo situado junto a **Propiedades de configuración** y seleccione **General**.  La ubicación de salida se especifica junto a **Directorio de resultados**.  Para obtener más información, vea [Página de propiedades General \(Proyecto\)](../ide/general-property-page-project.md).  
  
## Vea también  
 [Tipos de proyecto de Visual C\+\+](../ide/visual-cpp-project-types.md)