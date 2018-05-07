---
title: C2793 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2793
dev_langs:
- C++
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea378b2a875542eab431cf9cc30217f50c971af6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2793"></a>C2793 de Error del compilador
'token': siguiente token inesperado '::', identificador o la palabra clave 'operator' se esperaba  
  
 Los únicos tokens que pueden seguir `__super::` son un identificador o la palabra clave `operator`.  
  
 El ejemplo siguiente genera C2793  
  
```  
// C2793.cpp  
struct B {  
   void mf();  
};  
  
struct D : B {  
   void mf() {  
      __super::(); // C2793  
   }  
};  
```