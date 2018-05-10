---
title: Crear un cuadro de diálogo que los usuarios no puedan salir | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, creating
- modal dialog boxes, logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc04c9ccfb0fdc74e57142bf746681411bbba495
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="creating-a-dialog-box-that-users-cannot-exit"></a>Crear un cuadro de diálogo del que los usuarios no puedan salir
Puede crear un cuadro de diálogo en tiempo de ejecución del que un usuario no pueda salir. Este tipo de cuadro de diálogo es útil para inicios de sesión y para bloqueos de documentos o aplicaciones.  
  
### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>Par crear un cuadro de diálogo del que un usuario no pueda salir.  
  
1.  En el panel **Propiedades** para el cuadro de diálogo, establezca la propiedad **Menú del sistema** en **false**.  
  
     Esto deshabilita el menú del sistema del cuadro de diálogo y el botón **Cerrar** .  
  
2.  En el formulario del cuadro de diálogo, elimine los botones **Cancelar** y **Aceptar** .  
  
     En tiempo de ejecución, un usuario no puede salir de un cuadro de diálogo modal que tenga estas características.  
  
 Para habilitar la comprobación de este tipo de cuadro de diálogo, la función del cuadro de diálogo de prueba detecta cuando se presiona la tecla ESC. (A ESC también se le conoce como tecla virtual VK_ESCAPE). Independientemente de cómo se diseñe el comportamiento del cuadro de diálogo en tiempo de ejecución, puede finalizarlo en modo de prueba presionando ESC.  
  
> [!NOTE]
>  Para aplicaciones MFC, para crear un cuadro de diálogo del que los usuarios no puedan salir, debe invalidar el comportamiento predeterminado de `OnOK` y `OnCancel` porque si elimina los botones asociados, todavía se puede descartar el cuadro de diálogo presionando ENTRAR o ESC.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear un recurso](../windows/how-to-create-a-resource.md)   
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editor de cuadros de diálogo](../windows/dialog-editor.md)

