---
title: "ML Nonfatal Error A2096 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2096"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2096"
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2096
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**segmento, grupo, o registro de segmento esperado**  
  
 Un segmento o grupo era esperado pero no se encontró.  
  
 Uno de los siguientes a:  
  
-   El operando izquierdo especificado con el operador de reemplazo de segmento \(**:**\) no es un registro de segmento \(CS, DS, SS, IS, FS, o GS\), nombre de grupo, nombre de segmento, o expresión de segmento.  
  
-   La directiva de [ASSUME](../../assembler/masm/assume.md) se asignó un registro de segmento sin una dirección válida del segmento, el registro de segmento, el grupo, o grupo especial de **Plana** .  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)