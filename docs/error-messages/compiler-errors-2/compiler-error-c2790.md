---
title: "Error del compilador C2790 | Microsoft Docs"
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
  - "C2790"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2790"
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2790
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'super' : esta palabra clave sólo se puede utilizar en el cuerpo de la función miembro de clase  
  
 Este mensaje de error aparece si el usuario intenta utilizar la palabra clave [super](../../cpp/super.md) fuera del contexto de una función miembro.  
  
 El código siguiente genera el error C2790:  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```