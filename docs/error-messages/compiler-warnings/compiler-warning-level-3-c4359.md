---
title: "Advertencia del compilador (nivel 3) C4359 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4359"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4359"
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Advertencia del compilador (nivel 3) C4359
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': la alineación real \(8\) es mayor que el valor especificado en \_\_declspec \(alinee \(\)\)  
  
 La alineación especificada para un tipo es menor que la alineación del tipo de uno de sus miembros de datos.  Para obtener más información, vea [align](../../cpp/align-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4359.  
  
```  
// C4359.cpp  
// compile with: /W3 /c  
struct __declspec(align(8)) C8 { __int64 i; };  
struct __declspec(align(4)) C4  { C8 m8; };   // C4359  
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK  
struct __declspec(align(16)) C16  { C8 m8; };   // OK  
```