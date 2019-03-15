---
title: Procedimiento Configurar proyectos de Visual C++ para tener como destino de 64 bits, x64 plataformas
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 21c812efd101c64e250a545d2a40df6adc31c414
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813960"
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>Procedimiento Configurar proyectos de Visual C++ para tener como destino de 64 bits, x64 plataformas

Puede usar las configuraciones de proyecto en el IDE de Visual Studio para configurar las aplicaciones de C++ para tener como destino de 64 bits, x64 plataformas. También puede migrar la configuración de proyecto de Win32 en una configuración de proyecto de 64 bits.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Para configurar las aplicaciones de C++ para plataformas de 64 bits como destino

1. Abra el proyecto de C++ que quiera configurar.

1. Abra las páginas de propiedades de ese proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](working-with-project-properties.md).

   > [!NOTE]
   > Para los proyectos. NET, asegúrese de que el **propiedades de configuración** nodo, o uno de sus nodos secundarios, está seleccionado en el  **\<NombreDelProyecto > páginas de propiedades** cuadro de diálogo; en caso contrario, el  **Administrador de configuración** botón sigue sin estar disponible.

1. Elija el botón **Administrador de configuración** para abrir el cuadro de **diálogo del mismo nombre**.

1. En el **plataforma de soluciones activas** lista desplegable, seleccione el  **\<nuevo... >** opción para abrir el **nueva plataforma de solución** cuadro de diálogo.

1. En el **escriba o seleccione la nueva plataforma** lista desplegable, seleccione 64 bits de plataforma de destino.

   > [!NOTE]
   > En el cuadro de diálogo **Nueva plataforma de solución** , puede usar la opción **Copiar configuración de** para copiar la configuración del proyecto existente en la nueva configuración de proyecto de 64 bits.

1. Elija el botón **Aceptar** . La plataforma que seleccionó en el paso anterior aparece en **Plataforma de soluciones activas** en el cuadro de diálogo **Administrador de configuración** .

1. Elija la **cerrar** situado en la **Configuration Manager** diálogo cuadro y, a continuación, elija el **Aceptar** situado en la  **\<Projectname > Páginas de propiedades** cuadro de diálogo.

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Para copiar la configuración de proyecto de Win32 en una configuración de proyecto de 64 bits

- Cuando esté abierto el cuadro de diálogo **Nueva plataforma de solución** mientras configure un proyecto para una plataforma de 64 bits como destino, en la lista desplegable **Copiar configuración de** , seleccione **Win32**. Esta configuración de proyecto se actualizará automáticamente en el nivel de proyecto:

  - La opción de enlazador [/MACHINE](reference/machine-specify-target-platform.md) se establece en **/MACHINE:X64**.

  - La opción**Registrar resultados** está desactivada. Para obtener más información, consulta [Linker Property Pages](reference/linker-property-pages.md).

  - **Entorno de destino** se establece en **/env x64**. Para obtener más información, consulte [páginas de propiedades MIDL: General](reference/midl-property-pages-general.md).

  - Se borra**Validar parámetros** y restablece en el valor predeterminado. Para obtener más información, consulte [páginas de propiedades MIDL: Advanced](reference/midl-property-pages-advanced.md).

  - Si **Formato de la información de depuración** se estableció en **/ZI** en la configuración de proyecto de Win32, después, se establece en **/Zi** en la configuración de proyecto de 64 bits. Para obtener más información, consulte [/Z7, /Zi, /ZI (Formato de la información de depuración)](reference/z7-zi-zi-debug-information-format.md).

  > [!NOTE]
  > No se cambia ninguna de estas propiedades de proyecto si se sobrescriben en el nivel de archivo.

## <a name="see-also"></a>Vea también

[Configurar los proyectos de C++ de 64 bits, x64 destinos](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Depurar aplicaciones de 64 bits](/visualstudio/debugger/debug-64-bit-applications)
