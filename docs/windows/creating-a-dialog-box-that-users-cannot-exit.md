---
title: "Crear un cuadro de diálogo que los usuarios no puedan salir | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, creating
- modal dialog boxes, logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b53c233c13ed53f4cf2ccf489da9af90ae15796
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

