---
title: "Crear cuadros de di&#225;logo no modales | Microsoft Docs"
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
  - "cuadros de diálogo de MFC, crear"
  - "cuadros de diálogo de MFC, no modales"
  - "cuadros de diálogo no modales, crear"
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear cuadros de di&#225;logo no modales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para un cuadro de diálogo no modal, debe proporcionar dispone el constructor público en la clase de diálogo.  Para crear un cuadro de diálogo no modal, llame al constructor público y llame a la función miembro de [crear](../Topic/CDialog::Create.md) del diálogo para cargar el recurso de cuadro de diálogo.  Puede llamar a **crear** cualquiera durante o después de la llamada al constructor.  Si el recurso de cuadro de diálogo tiene la propiedad **WS\_VISIBLE**, aparece el cuadro de diálogo inmediatamente.  Si no, debe llamar a su función miembro de [ShowWindow](../Topic/CWnd::ShowWindow.md) .  
  
## Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)