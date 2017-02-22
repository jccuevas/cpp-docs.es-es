---
title: "ML Nonfatal Error A2008 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2008"
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Nonfatal Error A2008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**error de sintaxis:**  
  
 Un símbolo en la ubicación actual ha originado un error de sintaxis.  
  
 Uno de los siguientes podría haberse producido:  
  
-   Un prefijo de punto se agregó a u omitido de una directiva.  
  
-   Una palabra reservada \(como **C** o **CALIBRE**\) se utiliza como identificador.  
  
-   Una instrucción se utilizó que no estaba disponible con la selección de procesador actual de extracción o de uno.  
  
-   Se utilizó un operador de runtime de comparación \(como `==`\) en una instrucción de ensamblado condicional en lugar de un operador relacional \(como [EQ](../../assembler/masm/operator-eq.md)\).  
  
-   Una instrucción o una directiva se asignó demasiado pocos operandos.  
  
-   Una directiva obsoletos se utilizó.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)