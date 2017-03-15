---
title: "Error del compilador C2569 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2569"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2569"
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2569
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'EnumeraciónOUnión' : enum\/union no se pueden utilizar como clase base  
  
 Si tiene que derivar un tipo de la unión o enumeración especificadas, cambie la unión o enumeración por una clase o estructura.  
  
 El código siguiente genera el error C2569:  
  
```  
// C2569.cpp  
// compile with: /c  
union ubase {};  
class cHasPubUBase : public ubase {};   // C2569  
// OK  
struct sbase {};  
class cHasPubUBase : public sbase {};  
```