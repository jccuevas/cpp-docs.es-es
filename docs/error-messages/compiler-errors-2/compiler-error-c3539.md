---
title: "Error del compilador C3539 | Microsoft Docs"
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
  - "C3539"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3539"
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3539
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"tipo": un argumento de plantilla no puede ser de un tipo que contiene "auto"  
  
 El tipo de argumento de plantilla indicado no puede contener ningún uso de la palabra clave `auto`.  
  
### Para corregir este error  
  
1.  No especifique el argumento de plantilla con la palabra clave `auto`.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3539.  
  
```  
// C3539.cpp  
// Compile with /Zc:auto  
template<class T> class C{};  
int main()  
{  
   C<auto> c;   // C3539  
   return 0;  
}  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)