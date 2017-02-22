---
title: "Error del compilador C2891 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2891"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2891"
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2891
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parámetro': no puede adquirir la dirección de un parámetro de plantilla  
  
 En lugar de utilizar este código:  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 utilice este otro:  
  
```  
template <int i> int* f() { return i; }  
```