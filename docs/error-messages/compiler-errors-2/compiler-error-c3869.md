---
title: "Error del compilador C3869 | Microsoft Docs"
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
  - "C3869"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3869"
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3869
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la restricción gcnew no tiene lista de parámetros vacía ' \(\)'  
  
 La restricción `gcnew` especial se especificó sin la lista de parámetros vacía.  Para obtener más información, vea [Restricciones de parámetros de tipo genérico \(C\+\+\/CLI\)](../Topic/Constraints%20on%20Generic%20Type%20Parameters%20\(C++-CLI\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3869.  
  
```  
// C3869.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : gcnew   // C3869  
// try the following line instead  
// where T : gcnew()  
ref class List {};  
```