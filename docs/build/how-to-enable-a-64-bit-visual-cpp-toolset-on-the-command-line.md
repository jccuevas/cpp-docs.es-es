---
title: "C&#243;mo: Habilitar un conjunto de herramientas de Visual C++ de 64 bits en la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compilador de 64 bits [C++], uso de la línea de comandos"
  - "compilador de 64 bits [C++], conjunto de herramientas habilitado en la línea de comandos"
  - "línea de comandos [C++], compilador de 64 bits"
  - "IPF"
  - "IPF, compilador de línea de comandos"
  - "Itanium [C++]"
  - "Itanium [C++], compilador de línea de comandos"
  - "x64 [C++]"
  - "x64 [C++], compilador de línea de comandos"
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Habilitar un conjunto de herramientas de Visual C++ de 64 bits en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ incluye compiladores que puede utilizar para crear aplicaciones que se ejecutan en un sistema operativo Windows de 32 bits, 64 bits o basado en ARM.  
  
> [!NOTE]
>  Para obtener información sobre las herramientas específicas que se incluyen con cada edición de Visual C\+\+, vea [Herramientas y plantillas de Visual C\+\+ en las versiones de Visual Studio](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md).  
>   
>  Para más información sobre cómo usar el IDE de Visual Studio para crear aplicaciones de 64 bits, vea [Cómo: Configurar proyectos de Visual C\+\+ en plataformas de 64 bits de destino](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] incluye compiladores de 32 bits, hospedados en x86, nativos y cruzados para destinos x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] y ARM.  Cuando se instala [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] en un sistema operativo Windows de 64 bits, los compiladores nativos y cruzados 32 bits, hospedados en x86, así como los compiladores nativos y cruzados de 64 bits, hospedados en [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], se instalan para cada destino \(x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] y ARM\).  Los compiladores de 32 bits y 64 bits para cada destino generan código idéntico, pero los de 64 bits admiten más memoria para los símbolos de encabezado precompilados y las opciones de Optimización de todo el programa \([\/GL](../build/reference/gl-whole-program-optimization.md), [\/LTCG](../build/reference/ltcg-link-time-code-generation.md)\).  Si se ejecuta con límites de memoria cuando usa un compilador de 32 bits, pruebe el compilador de 64 bits.  
  
 Cuando Visual Studio está instalado en un sistema operativo Windows de 64 bits, hay disponibles más métodos abreviados del símbolo de sistema para algunos de los compiladores nativos de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] y compiladores cruzados x86 de 64 bits.  Para tener acceso a estos símbolos del sistema en Windows 8, en la pantalla **Inicio**, abra **Todas las aplicaciones**.  En la versión instalada de **[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]**, abra **Visual Studio Tools** y elija uno de los símbolos del sistema, ya sea nativo de la herramienta o entre herramientas.  En versiones anteriores de Windows, elija **Inicio**, expanda **Todos los programas**, **[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]**, **Visual Studio Tools** y, a continuación, elija un símbolo del sistema.  
  
## vcvarsall.bat  
 Cualquiera de los compiladores se puede usar en la línea de comandos ejecutando el archivo de comandos vcvarsall.bat para configurar la ruta de acceso y las variables de entorno que habilitan el conjunto de herramientas del compilador.  Dado que no existen métodos abreviados del símbolo de sistema que habiliten un conjunto de herramientas de 64 bits que tenga como destino plataformas x86 o de ARM, utilice en su lugar vcvarsall.bat en una ventana de símbolo del sistema para que se use el conjunto de herramientas de 64 bits.  Para obtener más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
 Con los siguientes pasos se explica cómo configurar un símbolo del sistema para usar el conjunto de herramientas nativo de 64 bits que tenga como destino plataformas x86, x64 y ARM.  
  
#### Para ejecutar vcvarsall.bat para usar un conjunto de herramientas de 64 bits  
  
1.  En el símbolo del sistema, cambie al directorio de instalación [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] \(la ubicación dependerá del sistema y de la instalación de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], si bien una habitual suele ser C:\\Archivos de programa \(x86\)\\Microsoft Visual Studio *versión*\\VC\\\). Escriba lo siguiente, por ejemplo:  
  
     cd "\\Archivos de programa \(x86\)\\Microsoft Visual Studio 12.0\\VC"  
  
2.  Para configurar esta ventana de símbolo del sistema para compilaciones de línea de comandos de 64 bits que tienen que como destino plataformas x64, escriba lo siguiente en el símbolo del sistema:  
  
     `vcvarsall amd64`  
  
3.  Para configurar esta ventana de símbolo del sistema para compilaciones de línea de comandos de 64 bits que tienen que como destino plataformas x86, escriba lo siguiente en el símbolo del sistema:  
  
     `vcvarsall amd64_x86`  
  
4.  Para configurar esta ventana de símbolo del sistema para compilaciones de línea de comandos de 64 bits que tienen que como destino plataformas ARM, escriba lo siguiente en el símbolo del sistema:  
  
     `vcvarsall amd64_arm`  
  
## Vea también  
 [Configurar programas de 64 bits](../build/configuring-programs-for-64-bit-visual-cpp.md)