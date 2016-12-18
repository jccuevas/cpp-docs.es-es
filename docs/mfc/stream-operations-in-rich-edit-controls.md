---
title: "Operaciones de secuencia en los controles Rich Edit | Microsoft Docs"
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
  - "CRichEditCtrl (clase), operaciones con secuencias"
  - "CRichEditCtrl (clase), almacenamiento con secuencias"
  - "controles Rich Edit, operaciones con secuencias"
  - "almacenamiento, secuencia en CRichEditCtrl"
  - "operaciones con secuencias en CRichEditCtrl"
  - "almacenamiento con secuencias y CRichEditCtrl"
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operaciones de secuencia en los controles Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar secuencias para transferir datos en o de un control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\).  Una secuencia se define mediante una estructura de [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) , que especifica un búfer y una función de devolución de llamada definido por la aplicación.  
  
 Para leer datos de un control rich edit \(es decir, secuencia los datos en\), utilice la función miembro de [StreamIn](../Topic/CRichEditCtrl::StreamIn.md) .  El control llama repetidamente la función de devolución de llamada definido por la aplicación, que transfiere una parte de los datos en el búfer cada vez.  
  
 Para guardar el contenido de un control rich edit \(es decir, secuencia los datos out\), puede utilizar la función miembro de [StreamOut](../Topic/CRichEditCtrl::StreamOut.md) .  El control escribe repetidamente en el búfer y después llama a la función de devolución de llamada definido por la aplicación.  Para cada llamada, la función de devolución de llamada guarda el contenido del búfer.  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)