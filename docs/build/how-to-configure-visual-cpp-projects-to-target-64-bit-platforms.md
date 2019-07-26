---
title: Procedimiento Configuración de proyectos C++ de Visual Studio para plataformas de destino de 64 bits x64
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 762fd5d6ddbb55713cf2fc5e34cb33fb91b08eb9
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492237"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>Procedimiento Configuración de proyectos C++ de Visual Studio para plataformas de destino de 64 bits x64

Puede usar las configuraciones de proyecto en el IDE de Visual Studio para configurar C++ aplicaciones para plataformas de 64 bits x64 de destino. También puede migrar la configuración de proyecto de Win32 en una configuración de proyecto de 64 bits.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Para configurar las aplicaciones de C++ para plataformas de 64 bits como destino

1. Abra el proyecto de C++ que quiera configurar.

1. Abra las páginas de propiedades de ese proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](working-with-project-properties.md).

   > [!NOTE]
   > En el caso de los proyectos .net, asegúrese de que el nodo **propiedades de configuración** , o uno de sus nodos secundarios, está seleccionado en el   **\<cuadro de diálogo nombreDeProyecto > páginas de propiedades** ; de lo contrario, el botón Configuration Manager permanece dispone.

1. Elija el botón **Administrador de configuración** para abrir el cuadro de **diálogo del mismo nombre**.

1. En la lista desplegable **plataforma de soluciones activas** , seleccione el  **\<nuevo... >** opción para abrir el cuadro de diálogo **nueva plataforma de solución** .

1. En la lista desplegable **Escriba o seleccione la nueva plataforma** , seleccione una plataforma de destino de 64 bits.

   > [!NOTE]
   > En el cuadro de diálogo **Nueva plataforma de solución** , puede usar la opción **Copiar configuración de** para copiar la configuración del proyecto existente en la nueva configuración de proyecto de 64 bits.

1. Elija el botón **Aceptar** . La plataforma que seleccionó en el paso anterior aparece en **Plataforma de soluciones activas** en el cuadro de diálogo **Administrador de configuración** .

1. Elija el botón **cerrar** del cuadro de diálogo **Configuration Manager** y, a continuación, elija el botón **Aceptar** en el cuadro de diálogo  **\<nombreDeProyecto > páginas de propiedades** .

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Para copiar la configuración de proyecto de Win32 en una configuración de proyecto de 64 bits

- Cuando esté abierto el cuadro de diálogo **Nueva plataforma de solución** mientras configure un proyecto para una plataforma de 64 bits como destino, en la lista desplegable **Copiar configuración de** , seleccione **Win32**. Esta configuración de proyecto se actualizará automáticamente en el nivel de proyecto:

  - La opción de enlazador [/MACHINE](reference/machine-specify-target-platform.md) se establece en **/MACHINE:X64**.

  - La opción**Registrar resultados** está desactivada. Para obtener más información, consulta [Linker Property Pages](reference/linker-property-pages.md).

  - **Entorno de destino** se establece en **/env x64**. Para obtener más información, consulte [las páginas de propiedades MIDL](reference/midl-property-pages.md).

  - Se borra**Validar parámetros** y restablece en el valor predeterminado. Para obtener más información, consulte [las páginas de propiedades MIDL](reference/midl-property-pages.md).

  - Si **Formato de la información de depuración** se estableció en **/ZI** en la configuración de proyecto de Win32, después, se establece en **/Zi** en la configuración de proyecto de 64 bits. Para obtener más información, consulte [/Z7, /Zi, /ZI (Formato de la información de depuración)](reference/z7-zi-zi-debug-information-format.md).

  > [!NOTE]
  > No se cambia ninguna de estas propiedades de proyecto si se sobrescriben en el nivel de archivo.

## <a name="see-also"></a>Vea también

[Configuración de proyectos de Visual C++ para destinos x64 de 64 bits](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Depurar aplicaciones de 64 bits](/visualstudio/debugger/debug-64-bit-applications)
