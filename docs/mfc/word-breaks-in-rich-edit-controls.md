---
title: "Separaciones de palabras en los controles Rich Edit | Microsoft Docs"
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
  - "separar palabras en CRichEditCtrl"
  - "CRichEditCtrl (clase), se separa la palabra en"
  - "controles Rich Edit, se separa la palabra en"
  - "se separa la palabra"
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Separaciones de palabras en los controles Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) llama a una función denominada “un procedimiento de la interrupción de la palabra” para buscar interrupciones entre las palabras y determinar donde puede líneas de interrupción.  El control utiliza esta información al realizar operaciones de ajuste automático de línea y al procesar las combinaciones de teclas CTRL\+FLECHA IZQUIERDA y DERECHA.  Una aplicación puede enviar mensajes a un control rich edit para reemplazar el procedimiento predeterminado de división de palabras, para recuperar información de división de palabras, y para determinar en qué línea está un carácter especificado.  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)