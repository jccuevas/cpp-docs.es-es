---
title: "Error del evaluador de expresiones CXX0019 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0019"
  - "CXX0019"
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

conversión de tipo errónea  
  
 El evaluador de la expresión C no puede realizar la conversión de tipo escrita.  
  
 Este error es idéntico a CAN0019.  
  
### Posibles causas del error:  
  
1.  El tipo especificado es desconocido.  
  
2.  Había demasiados niveles de tipos de puntero.  Por ejemplo, la conversión de tipo  
  
    ```  
    (char **)h_message  
    ```  
  
     no se puede evaluar mediante el evaluador de la expresión C.