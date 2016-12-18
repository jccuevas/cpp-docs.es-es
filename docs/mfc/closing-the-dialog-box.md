---
title: "Cerrar el cuadro de di&#225;logo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "cuadros de diálogo, cerrar"
  - "cuadros de diálogo de MFC, cerrar"
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cerrar el cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un cuadro de diálogo modal se cierra cuando el usuario elige uno de los botones, normalmente el botón ACEPTAR o el botón Cancelar.  Elegir del botón ACEPTAR o cancelar hace que Windows para enviar el objeto de diálogo un mensaje de la CONTROL\- notificación de **BN\_CLICKED** con el identificador del botón, **IDOK** o **IDCANCEL**.  `CDialog` proporciona funciones predeterminadas del controlador para estos mensajes: `OnOK` y `OnCancel`.  Controladores predeterminados llaman a la función miembro de `EndDialog` para cerrar la ventana de cuadro de diálogo.  También puede llamar `EndDialog` del propio código.  Para obtener más información, vea la función miembro de [EndDialog](../Topic/CDialog::EndDialog.md) de la clase `CDialog` en *la referencia de MFC*.  
  
 Para organizar para cerrar y eliminar un cuadro de diálogo, un reemplazo no modal `PostNcDestroy` e invocar el operador de **borrar** en el puntero de **this** .  [Destrucción del cuadro de diálogo](../mfc/destroying-the-dialog-box.md) explica lo que ocurrirá a continuación.  
  
## Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)