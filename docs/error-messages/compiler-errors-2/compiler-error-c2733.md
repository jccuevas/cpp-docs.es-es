---
title: C2733 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2733
dev_langs:
- C++
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc1857cd800dd2d395754b9ae95094d9f57aad27
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2733"></a>C2733 de Error del compilador
segunda vinculación C de la función sobrecargada 'función' no permitida  
  
 Más de una función sobrecargada se declara con una vinculación C. Al utilizar la vinculación de C, un único formato de una función especificada puede ser externo. Dado que las funciones sobrecargadas tienen el mismo nombre no representativo, que no pueden utilizarse con los programas de C.  
  
 El ejemplo siguiente genera C2733:  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```