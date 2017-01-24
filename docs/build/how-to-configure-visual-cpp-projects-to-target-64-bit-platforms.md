---
title: "C&#243;mo: Configurar proyectos de Visual C++ en plataformas de 64 bits de destino | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "plataformas [C++], 64 bits"
  - "programación de 64 bits [C++], configurar proyectos"
  - "configuraciones de proyectos [C++]"
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Configurar proyectos de Visual C++ en plataformas de 64 bits de destino
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede usar las configuraciones de proyecto en Visual Studio para configurar las aplicaciones de C\+\+ para plataformas de 64 bits de destino. También puede migrar la configuración de proyecto de Win32 en una configuración de proyecto de 64 bits.  
  
### Para configurar las aplicaciones de C\+\+ para plataformas de 64 bits como destino  
  
1.  Abra el proyecto de C\+\+ que quiera configurar.  
  
2.  Abra las páginas de propiedades de ese proyecto. Para obtener más información, consulta [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md).  
  
    > [!NOTE]
    >  Para proyectos .NET, asegúrese de que el nodo **Propiedades de configuración**, o uno de sus nodos secundarios, está seleccionado en el cuadro de diálogo **Páginas de propiedades de \<NombreDeProyecto\>**; en caso contrario, el botón **Administrador de configuración** seguirá sin estar disponible.  
  
3.  Elija el botón **Administrador de configuración** para abrir el cuadro de diálogo del mismo nombre.  
  
4.  En la lista desplegable **Plataforma de soluciones activas**, seleccione la opción **\<Nueva...\>** para abrir el cuadro de diálogo **Nueva plataforma de solución**.  
  
5.  En la lista desplegable **Escriba o seleccione la nueva plataforma**, seleccione una plataforma de 64 bits.  
  
    > [!NOTE]
    >  En el cuadro de diálogo **Nueva plataforma de solución**, puede usar la opción **Copiar configuración de** para copiar la configuración del proyecto existente en la nueva configuración de proyecto de 64 bits.  
  
6.  Elija el botón **Aceptar**. La plataforma que seleccionó en el paso anterior aparece en **Plataforma de soluciones activas** en el cuadro de diálogo **Administrador de configuración**.  
  
7.  Elija el botón **Cerrar** en el cuadro de diálogo **Administrador de configuración** y luego elija el botón **Aceptar** del cuadro de diálogo **Páginas de propiedades de \<NombreDeProyecto\>**.  
  
### Para copiar la configuración de proyecto de Win32 en una configuración de proyecto de 64 bits  
  
-   Cuando esté abierto el cuadro de diálogo **Nueva plataforma de solución** mientras configure un proyecto para una plataforma de 64 bits como destino, en la lista desplegable **Copiar configuración de**, seleccione **Win32**. Esta configuración de proyecto se actualizará automáticamente en el nivel de proyecto:  
  
    -   La opción de enlazador [\/MACHINE](../build/reference/machine-specify-target-platform.md) se establece en **\/MACHINE:X64**.  
  
    -   La opción **Registrar resultados** está desactivada. Para obtener más información, consulta [Páginas de propiedades Vinculador](../ide/linker-property-pages.md).  
  
    -   **Entorno de destino** se establece en **\/env x64**. Para obtener más información, consulta [Páginas de propiedades MIDL: General](../ide/midl-property-pages-general.md).  
  
    -   Se borra **Validar parámetros** y restablece en el valor predeterminado. Para obtener más información, consulta [Páginas de propiedades MIDL: Avanzadas](../ide/midl-property-pages-advanced.md).  
  
    -   Si **Formato de la información de depuración** se estableció en **\/ZI** en la configuración de proyecto de Win32, después, se establece en **\/Zi** en la configuración de proyecto de 64 bits. Para obtener más información, consulta [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../build/reference/z7-zi-zi-debug-information-format.md).  
  
    > [!NOTE]
    >  No se cambia ninguna de estas propiedades de proyecto si se sobrescriben en el nivel de archivo.  
  
## Vea también  
 [Aplicaciones de 64 bits](../Topic/64-bit%20Applications.md)   
 [Configurar programas de 64 bits](../build/configuring-programs-for-64-bit-visual-cpp.md)   
 [Depurar aplicaciones de 64 bits](../Topic/Debug%2064-Bit%20Applications.md)