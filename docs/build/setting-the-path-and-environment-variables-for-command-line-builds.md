---
title: "Establecer la ruta de acceso y las variables de entorno para compilar desde la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "include"
  - "Lib"
  - "Path"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador) [C++], variables de entorno"
  - "compilar código fuente [C++], desde la línea de comandos"
  - "variables de entorno [C++]"
  - "variables de entorno [C++], compilador CL"
  - "INCLUDE (palabra reservada)"
  - "LIB (variable de entorno)"
  - "LINK (herramienta) [C++], variables de entorno"
  - "LINK (herramienta) [C++], ruta de acceso"
  - "PATH (palabra reservada)"
  - "VCVARS32.bat: archivo"
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
caps.latest.revision: 17
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Establecer la ruta de acceso y las variables de entorno para compilar desde la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las herramientas de compilación de línea de comandos de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] requieren diversas variables de entorno que estén personalizadas para su instalación.  Cuando [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] se instala, crea archivos de comandos que establecen las variables de entorno necesarias y, luego, crea accesos directos que inician una ventana del símbolo del sistema donde ya están establecidas esas variables.  Cuando quiera usar las herramientas de línea de comandos, puede ejecutar uno de estos accesos directos o abrir una ventana del símbolo del sistema convencional y, después, ejecutar el archivo de comandos vcvarsall.bat.  
  
 Las herramientas de línea de comandos de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] emplean las variables de entorno PATH, TMP, INCLUDE, LIB y LIBPATH y también pueden utilizar variables de entorno específicas de la herramienta.  Dado que los valores de estas variables de entorno son específicos de su instalación, y que las actualizaciones del producto pueden cambiarlos, le recomendamos que use un acceso directo del Símbolo del sistema para desarrolladores o vcvarsall.bat en lugar de establecerlos por su cuenta.  Para obtener información sobre las variables de entorno concretas utilizadas por el compilador y el enlazador, consulte [Variables de entorno de CL](../build/reference/cl-environment-variables.md) y [Variables de entorno de LINK](../build/reference/link-environment-variables.md).  
  
> [!NOTE]
>  Hay varias herramientas de línea de comandos u opciones de herramientas que requieren el permiso de administrador.  Para usarlas, le recomendamos que abra una ventana del símbolo del sistema con la opción **Ejecutar como administrador** \(en el menú contextual de la ventana del símbolo del sistema que quiera abrir\).  
  
## Uso de los accesos directos del símbolo del sistema  
 El acceso directo del Símbolo del sistema para desarrolladores incluido en todas las ediciones de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] abre una ventana del símbolo del sistema y establece el entorno de modo que utilice el conjunto de herramientas nativo x86 de 32 bits para dirigirse a los procesadores x86.  También hay disponibles símbolos del sistema para compiladores cruzados de 32 bits que se dirigen a las plataformas x64 y ARM.  Además, en función del sistema y de la edición de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalada, es posible que esté disponible un acceso directo del símbolo del sistema para un conjunto de herramientas nativo x64 de 64 bits que se dirige a los procesadores x64 y uno para compiladores cruzados de 64 bits que se dirige a los procesadores x86.  Estas versiones del conjunto de herramientas de línea de comandos están disponibles en todas las ediciones de Visual Studio:  
  
 x86 en x86  
 Utilice este conjunto de herramientas para crear archivos de salida para máquinas x86.  Se ejecuta como un proceso de 32 bits, nativo en una máquina de x86 y bajo WOW64 en los sistemas operativos Windows de 64 bits.  
  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] en x86 \(compilador cruzado de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]\)  
 Utilice este conjunto de herramientas para crear archivos de salida para [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  Se ejecuta como un proceso de 32 bits, nativo en una máquina de x86 y bajo WOW64 en los sistemas operativos Windows de 64 bits.  
  
 ARM en x86 \(compilador cruzado de ARM\)  
 Utilice este conjunto de herramientas para crear archivos de salida para máquinas ARM.  Se ejecuta como un proceso de 32 bits, nativo en una máquina de x86 y bajo WOW64 en los sistemas operativos Windows de 64 bits.  
  
 Estas versiones del conjunto de herramientas de línea de comandos están disponibles en las plataformas de 64 bits:  
  
 x86 en [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]  
 Utilice este conjunto de herramientas para crear archivos de salida para máquinas x86.  Se ejecuta como un proceso nativo en los sistemas operativos Windows de 64 bits.  
  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] en [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]  
 Utilice este conjunto de herramientas para crear archivos de salida para máquinas [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  Se ejecuta como un proceso nativo en los sistemas operativos Windows de 64 bits.  
  
 ARM en x64 \(compilador cruzado de ARM\)  
 Utilice este conjunto de herramientas para crear archivos de salida para máquinas ARM.  Se ejecuta como un proceso de 64 bits nativo en los sistemas operativos Windows de 64 bits.  
  
#### Para abrir una ventana del Símbolo del sistema para desarrolladores  
  
1.  Con la pantalla Inicio de Windows 8 visible, escriba Visual Studio Tools.  Observe que los resultados de búsqueda cambian a medida que escribe. Cuando aparezca **Visual Studio Tools**, elíjalo.  
  
     En las versiones anteriores de Windows, elija **Inicio** y, luego, en el cuadro de búsqueda, escriba Visual Studio Tools.  Cuando aparezca **Visual Studio Tools** en los resultados de la búsqueda, elíjalo.  
  
2.  En la carpeta **Visual Studio Tools**, abra el **Símbolo del sistema para desarrolladores** de su versión de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  \(Para ejecutarlo como administrador, abra el menú contextual del Símbolo del sistema para desarrolladores y elija **Ejecutar como administrador**\).  
  
 El Símbolo del sistema para desarrolladores establece el entorno de modo que utilice el conjunto de herramientas nativo de 32 bits para dirigirse a los procesadores x86.  Elija el **símbolo del sistema de las herramientas cruzadas de x64** para usar el conjunto de herramientas nativo de 32 bits para dirigirse a los procesadores x64.  Elija el **símbolo del sistema de las herramientas cruzadas de ARM** para usar el conjunto de herramientas nativo de 32 bits para dirigirse a los procesadores ARM.  Elija el **símbolo del sistema de las herramientas nativas de x64** para usar el conjunto de herramientas nativo de 64 bits para dirigirse a los procesadores x64.  
  
## Uso de vcvarsall.bat en una ventana del símbolo del sistema  
 Si ejecuta vcvarsall.bat en una ventana del símbolo del sistema convencional, puede establecer variables de entorno con el fin de configurar la línea de comandos para la compilación nativa de 32 o 64 bits, o la compilación cruzada para procesadores x86, x64 o ARM.  Si no se proporcionan argumentos, vcvarsall.bat configura las variables de entorno para utilizar el compilador nativo de 32 bits para los destinos de x86.  Sin embargo, puede utilizarlo para configurar cualquier compilador.  Si especifica una configuración del compilador que no se instala ni está disponible en la arquitectura de su equipo de compilación, se mostrará un mensaje de error.  La tabla siguiente muestra los argumentos compatibles.  
  
|Argumento de vcvarsall.bat|Compilador|Arquitectura del equipo de compilación|Arquitectura de salida de compilación|  
|--------------------------------|----------------|--------------------------------------------|-------------------------------------------|  
|x86|x86 nativo de 32 bits|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|x86|  
|x86\_amd64|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] en x86 cruzado|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|x86\_arm|ARM en x86 cruzado|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|ARM|  
|amd64|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] nativo de 64 bits|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|amd64\_x86|x86 en [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] cruzado|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|x86|  
|amd64\_arm|ARM en [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] cruzado|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|ARM|  
  
 Los siguientes pasos muestran cómo configurar un símbolo del sistema con el fin de utilizar un conjunto de herramientas nativo de 32 bits para dirigirse a las plataformas x86.  
  
#### Para ejecutar vcvarsall.bat  
  
1.  En el símbolo del sistema, cambie al directorio de instalación de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  \(La ubicación depende del sistema y de la instalación de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], pero una instalación típica es C:\\Archivos de programa \(x86\)\\Microsoft Visual Studio *versión*\\VC\\\). Por ejemplo, escriba:  
  
     cd "\\Archivos de programa \(x86\)\\Microsoft Visual Studio 12.0\\VC"  
  
2.  Para configurar esta ventana del símbolo del sistema para las compilaciones de línea de comandos x86 de 32 bits, en el símbolo del sistema, escriba:  
  
     `vcvarsall x86`  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] también ofrece vcvars32.bat para configurar un entorno de línea de comandos.  El archivo vcvars32.bat se limita a establecer las variables de entorno apropiadas para habilitar las compilaciones desde la línea de comandos x86 de 32 bits.  Es el equivalente al comando `vcvarsall x86`.  
  
 Si utiliza [DEVENV](../Topic/Devenv%20Command%20Line%20Switches.md) para las compilaciones desde la línea de comandos, el entorno establecido por vcvarsall.bat o vcvars32.bat no afectará a sus compilaciones, salvo que especifique también la opción **\/useenv**.  
  
> [!CAUTION]
>  El archivo vcvarsall.bat puede variar de un equipo a otro.  Si el archivo vcvarsall.bat falta o está dañado, no lo reemplace por un archivo de otro equipo.  Vuelva a ejecutar el programa de instalación de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] para reemplazar el archivo que falta.  
>   
>  El archivo vcvarsall.bat también puede variar de una versión a otra.  Si la versión actual de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] está instalada en un equipo que también tiene una versión anterior de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)], no ejecute los archivos vcvarsall.bat ni vcvars32.bat de diferentes versiones en la misma ventana del símbolo del sistema.  
  
## Vea también  
 [Compilar en la línea de comandos](../build/building-on-the-command-line.md)   
 [Vinculación](../build/reference/linking.md)   
 [Opciones del vinculador](../build/reference/linker-options.md)   
 [Compilar un programa escrito en C\/C\+\+](../build/reference/compiling-a-c-cpp-program.md)   
 [Opciones del compilador](../build/reference/compiler-options.md)