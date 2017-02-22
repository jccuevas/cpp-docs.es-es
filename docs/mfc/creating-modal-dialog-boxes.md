---
title: "Crear cuadros de di&#225;logo modales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cuadros de diálogo de MFC, crear"
  - "cuadros de diálogo de MFC, modales"
  - "cuadros de diálogo modales, crear"
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Crear cuadros de di&#225;logo modales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para crear un cuadro de diálogo modal, llame a cualquiera de los dos constructores públicos declarados en [CDialog](../mfc/reference/cdialog-class.md).  A continuación, llama a la función miembro de [DoModal](../Topic/CDialog::DoModal.md) de objeto de cuadro de diálogo para mostrar el cuadro de diálogo y para administrar la interacción con ella hasta que el usuario elija ACEPTAR o cancelar.  Esta administración por `DoModal` es lo que hace que el cuadro de diálogo modal.  Para los cuadros de diálogo modales, `DoModal` carga el recurso de cuadro de diálogo.  
  
## Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)