---
title: "Advertencia del compilador (nivel 1) C4716 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4716"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4716"
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 1) C4716
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' debe devolver un valor  
  
 La función especificada no devolvió ningún valor.  
  
 Sólo las funciones con un tipo de valor devuelto void pueden usar el comando de devolución sin un valor devuelto correspondiente.  
  
 Se devolverá un valor no definido cuando se llame a esta función.  
  
 Esta advertencia suele convertirse automáticamente en un error.  Si desea modificar este comportamiento, use [\#pragma warning](../../preprocessor/warning.md).  
  
 El código siguiente genera el error C4716:  
  
```  
// C4716.cpp  
// compile with: /c /W1  
// C4716 expected  
#pragma warning(default:4716)  
int test() {  
   // uncomment the following line to resolve  
   // return 0;  
}  
```