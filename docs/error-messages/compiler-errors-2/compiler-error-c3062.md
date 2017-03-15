---
title: "Error del compilador C3062 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3062"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3062"
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3062
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'enumeración': el enumerador requiere un valor porque el tipo subyacente es 'tipo'  
  
 Puede especificar un tipo subyacente para una enumeración.  Sin embargo, algunos tipos requieren que se asignen valores a cada enumerador.  
  
 Para obtener más información sobre las enumeraciones, vea [Enum \(clase\)](../../windows/enum-class-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3062:  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```