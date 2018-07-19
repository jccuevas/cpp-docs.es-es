---
title: Error del compilador C3210 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3210
dev_langs:
- C++
helpviewer_keywords:
- C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24146139fce7a1e42e112f913ab35ca425a9d5d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256524"
---
# <a name="compiler-error-c3210"></a>Error del compilador C3210
'type': declaración de acceso solo puede aplicarse a un miembro de clase base  
  
 A [mediante declaración](../../cpp/using-declaration.md) se especificó incorrectamente.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3210.  
  
```  
// C3210.cpp  
// compile with: /c  
struct A {  
protected:  
   int i;  
};  
  
struct B {  
   using A::i;   // C3210  
};  
  
struct C : public A {  
   using A::i;   // OK  
};  
```