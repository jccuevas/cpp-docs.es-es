---
title: "Creating a Dialog Box That Users Cannot Exit | Microsoft Docs"
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
  - "dialog boxes, creating"
  - "modal dialog boxes, logon screens"
  - "logon screens"
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a Dialog Box That Users Cannot Exit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede crear un cuadro de diálogo en tiempo de ejecución del que un usuario no pueda salir. Este tipo de cuadro de diálogo es útil para inicios de sesión y para bloqueos de documentos o aplicaciones.  
  
### Par crear un cuadro de diálogo del que un usuario no pueda salir.  
  
1.  En el panel **Propiedades** para el cuadro de diálogo, establezca la propiedad **Menú del sistema** en **false**.  
  
     Esto deshabilita el menú del sistema del cuadro de diálogo y el botón **Cerrar**.  
  
2.  En el formulario del cuadro de diálogo, elimine los botones **Cancelar** y **Aceptar**.  
  
     En tiempo de ejecución, un usuario no puede salir de un cuadro de diálogo modal que tenga estas características.  
  
 Para habilitar la comprobación de este tipo de cuadro de diálogo, la función del cuadro de diálogo de prueba detecta cuando se presiona la tecla ESC. \(A ESC también se le conoce como tecla virtual VK\_ESCAPE\). Independientemente de cómo se diseñe el comportamiento del cuadro de diálogo en tiempo de ejecución, puede finalizarlo en modo de prueba presionando ESC.  
  
> [!NOTE]
>  Para aplicaciones MFC, para crear un cuadro de diálogo del que los usuarios no puedan salir, debe invalidar el comportamiento predeterminado de `OnOK`y `OnCancel` porque si elimina los botones asociados, todavía se puede descartar el cuadro de diálogo presionando ENTRAR o ESC.  
  
 Para información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones de escritorio](../Topic/Resources%20in%20Desktop%20Apps.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [How to: Create a Resource](../windows/how-to-create-a-resource.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Dialog Editor](../mfc/dialog-editor.md)