---
title: Error irrecuperable C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 0315af63e9fdbbb0b136a85a23cb28936dee6836
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273557"
---
# <a name="fatal-error-c1010"></a>Error irrecuperable C1010

> final de archivo inesperado al buscar la directiva de encabezado precompilado. ¿Olvidó agregar ' #include *nombre*' al origen?

## <a name="remarks"></a>Comentarios

Un archivo de inclusión especificado por [/Yu](../../build/reference/yu-use-precompiled-header-file.md) no aparece en el archivo de código fuente. Esta opción está habilitada de forma predeterminada en muchos C++ tipos de proyecto de Visual Studio. El archivo de inclusión predeterminado especificado por esta opción es *PCH. h*o *stdafx. h* en Visual Studio 2017 y versiones anteriores.

En el entorno de Visual Studio, use uno de los métodos siguientes para resolver este error:

- Asegúrese de que no ha eliminado, cambiado de nombre o quitado accidentalmente el archivo de encabezado *PCH. h* o el archivo de código fuente *PCH. cpp* del proyecto actual. (En proyectos anteriores, estos archivos se pueden denominar *stdafx. h* y *stdafx. cpp*).

- Asegúrese de que el archivo de encabezado *PCH. h* o *stdafx. h* se incluye antes que cualquier otra directiva de código o preprocesador en los archivos de código fuente. (En Visual Studio, este archivo de encabezado se especifica mediante la propiedad de proyecto de **archivo de encabezado precompilado** ).

- Puede desactivar el uso de encabezados precompilados. Si desactiva los encabezados precompilados, puede afectar gravemente al rendimiento de la compilación.

### <a name="to-turn-off-precompiled-headers"></a>Para desactivar los encabezados precompilados

Para desactivar el uso de encabezados precompilados en un proyecto, siga estos pasos:

1. En la ventana **Explorador de soluciones** , haga clic con el botón secundario en el nombre del proyecto y, a continuación, elija **propiedades** para abrir el cuadro de diálogo **páginas de propiedades** del proyecto.

1. En el menú desplegable **configuración** , seleccione **todas las configuraciones**.

1. Seleccione las **propiedades** > de configuración Página de propiedades encabezados de > **C/C++** **precompilados** .

1. En la lista de propiedades, seleccione la lista desplegable de la propiedad de **encabezado precompilado** y, a continuación, elija **no usar encabezados precompilados**. Elija **Aceptar** para guardar los cambios.

1. En la ventana de **Explorador de soluciones** , haga clic con el botón secundario en el archivo de código fuente *PCH. cpp* del proyecto. (En proyectos anteriores, el archivo puede tener el nombre *stdafx. cpp*). Elija **excluir del proyecto** para quitarlo de la compilación.

1. Use el comando de menú **compilar** > **solución limpia** para cada configuración que cree para eliminar cualquier archivo *Nombre_proyecto. pch* en los directorios de compilación intermedios.

## <a name="see-also"></a>Vea también

[Archivos de encabezado precompilados](../../build/creating-precompiled-header-files.md)\
[/YC (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu (usar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md)