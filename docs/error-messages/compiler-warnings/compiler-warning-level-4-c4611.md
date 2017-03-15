---
title: "Advertencia del compilador (nivel 4) C4611 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4611"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4611"
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 4) C4611
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la interacción entre 'función' y la destrucción de objetos de C\+\+ no es transportable  
  
 En algunas plataformas, es posible que las funciones que incluyen **catch** no admitan la semántica de destrucción de objetos de C\+\+ cuando quedan fuera de ámbito.  
  
 Para prevenir cualquier comportamiento inesperado, evite el uso de **catch** en funciones que posean constructores y destructores.  
  
 Esta advertencia sólo se genera una vez; vea [pragma warning](../../preprocessor/warning.md).