---
title: Error del compilador C2500 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c05ffd59e415375dd3c7f94ae9bc377c0fc2b9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229227"
---
# <a name="compiler-error-c2500"></a>Error del compilador C2500
'identificador1': 'identificador2' ya es una clase base directa  
  
 Una clase o estructura aparece más de una vez en una lista de clases base.  
  
 Una base directa es una mencionada en la lista base. Una base indirecta es una clase base de una de las clases en la lista base.  
  
 Una clase no puede especificarse como una clase base directa más de una vez. Una clase puede utilizarse como una clase base indirecta más de una vez.  
  
 El ejemplo siguiente genera C2500:  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```