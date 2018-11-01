---
title: Creación de un cuadro de diálogo (C++) que los usuarios no puedan salir
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [C++], creating
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
ms.openlocfilehash: 83c6c099f3d39db66969371e2cf7ad99a7f08587
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579847"
---
# <a name="creating-a-dialog-box-c-that-users-cannot-exit"></a>Creación de un cuadro de diálogo (C++) que los usuarios no puedan salir

Puede crear un cuadro de diálogo en tiempo de ejecución del que un usuario no pueda salir. Este tipo de cuadro de diálogo es útil para inicios de sesión y para bloqueos de documentos o aplicaciones.

### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>Par crear un cuadro de diálogo del que un usuario no pueda salir.

1. En el panel **Propiedades** para el cuadro de diálogo, establezca la propiedad **Menú del sistema** en **false**.

   Esto deshabilita el menú del sistema del cuadro de diálogo y el botón **Cerrar** .

2. En el formulario del cuadro de diálogo, elimine los botones **Cancelar** y **Aceptar** .

   En tiempo de ejecución, un usuario no puede salir de un cuadro de diálogo modal que tenga estas características.

Para habilitar la comprobación de este tipo de cuadro de diálogo, la función de cuadro de diálogo de prueba detecta cuando **Esc** está presionado. (**Esc** es también conocida como tecla virtual VK_ESCAPE.) Independientemente de cómo el cuadro de diálogo está diseñado para comportarse en tiempo de ejecución, puede finalizarlo en modo de prueba presionando **Esc**.

> [!NOTE]
> Para aplicaciones MFC, para crear un cuadro de diálogo que los usuarios no puedan salir, debe invalidar el comportamiento predeterminado de `OnOK` y `OnCancel` porque si elimina los botones asociados, todavía se puede descartar el cuadro de diálogo presionando  **Escriba** o **Esc**.

Para obtener información acerca de cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Procedimiento para crear un recurso](../windows/how-to-create-a-resource.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)