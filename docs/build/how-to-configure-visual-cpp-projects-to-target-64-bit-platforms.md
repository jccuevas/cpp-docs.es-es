---
title: "Cómo: configurar proyectos de Visual C++ para tener como destino de 64 bits, x64 plataformas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e651d28af3bd8635691d6a54d6c4cca8eb8c160
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>Cómo: configurar proyectos de Visual C++ para tener como destino de 64 bits, x64 plataformas

Puede usar las configuraciones de proyecto en el IDE de Visual Studio para configurar las aplicaciones de C++ para tener como destino de 64 bits, x64 plataformas. También puede migrar la configuración de proyecto de Win32 en una configuración de proyecto de 64 bits.  
  
### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Para configurar las aplicaciones de C++ para plataformas de 64 bits como destino  
  
1.  Abra el proyecto de C++ que quiera configurar.  
  
2.  Abra las páginas de propiedades de ese proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
    > [!NOTE]
    >  Para los proyectos. NET, asegúrese de que el **propiedades de configuración** nodo, o uno de sus nodos secundarios, está seleccionado en el  **\<NombreDeProyecto > páginas de propiedades** cuadro de diálogo; en caso contrario, el  **Administrador de configuración** botón sigue sin estar disponible.  
  
3.  Elija el botón **Administrador de configuración** para abrir el cuadro de **diálogo del mismo nombre**.  
  
4.  En el **plataforma de soluciones activas** lista desplegable, seleccione la  **\<nuevo... >** opción para abrir el **nueva plataforma de solución** cuadro de diálogo.  
  
5.  En el **, escriba o seleccione la nueva plataforma** lista desplegable, seleccione 64 bits de plataforma de destino.  
  
    > [!NOTE]
    >  En el cuadro de diálogo **Nueva plataforma de solución** , puede usar la opción **Copiar configuración de** para copiar la configuración del proyecto existente en la nueva configuración de proyecto de 64 bits.  
  
6.  Elija el botón **Aceptar** . La plataforma que seleccionó en el paso anterior aparece en **Plataforma de soluciones activas** en el cuadro de diálogo **Administrador de configuración** .  
  
7.  Elija la **cerrar** botón en el **Configuration Manager** diálogo cuadro y, a continuación, elija la **Aceptar** botón en el  **\<NombreDeProyecto > Páginas de propiedades** cuadro de diálogo.  
  
### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Para copiar la configuración de proyecto de Win32 en una configuración de proyecto de 64 bits  
  
-   Cuando esté abierto el cuadro de diálogo **Nueva plataforma de solución** mientras configure un proyecto para una plataforma de 64 bits como destino, en la lista desplegable **Copiar configuración de** , seleccione **Win32**. Esta configuración de proyecto se actualizará automáticamente en el nivel de proyecto:  
  
    -   La opción de enlazador [/MACHINE](../build/reference/machine-specify-target-platform.md) se establece en **/MACHINE:X64**.  
  
    -   La opción**Registrar resultados** está desactivada. Para obtener más información, consulta [Linker Property Pages](../ide/linker-property-pages.md).  
  
    -   **Entorno de destino** se establece en **/env x64**. Para obtener más información, consulta [MIDL Property Pages: General](../ide/midl-property-pages-general.md).  
  
    -   Se borra**Validar parámetros** y restablece en el valor predeterminado. Para obtener más información, consulta [MIDL Property Pages: Advanced](../ide/midl-property-pages-advanced.md).  
  
    -   Si **Formato de la información de depuración** se estableció en **/ZI** en la configuración de proyecto de Win32, después, se establece en **/Zi** en la configuración de proyecto de 64 bits. Para obtener más información, consulte [/Z7, /Zi, /ZI (Formato de la información de depuración)](../build/reference/z7-zi-zi-debug-information-format.md).  
  
    > [!NOTE]
    >  No se cambia ninguna de estas propiedades de proyecto si se sobrescriben en el nivel de archivo.  
  
## <a name="see-also"></a>Vea también  

[Aplicaciones de 64 bits de .NET framework](/dotnet/framework/64-bit-apps)   
[Configurar Visual C++ de 64 bits, x64 destinos](../build/configuring-programs-for-64-bit-visual-cpp.md)   
[Depurar aplicaciones de 64 bits](/visualstudio/debugger/debug-64-bit-applications)