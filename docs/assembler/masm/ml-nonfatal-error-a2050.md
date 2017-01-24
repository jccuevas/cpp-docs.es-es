---
title: "ML Nonfatal Error A2050 | Microsoft Docs"
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
  - "A2050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2050"
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2050
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**número real o de BCD no permitido**  
  
 Un número \(real\) flotante o una constante de decimal \(BCD\) codificado en binario se utilizó distinto como de inicializador de los datos.  
  
 Uno de los siguientes a:  
  
-   Un número real o un BCD se utiliza en una expresión.  
  
-   Un número real utilizado para inicializar una directiva distinto de [dword](../../assembler/masm/dword.md), de [QWORD](../../assembler/masm/qword.md), o de [TBYTE](../../assembler/masm/tbyte.md).  
  
-   Un BCD utilizado para inicializar una directiva distinto de `TBYTE`.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)