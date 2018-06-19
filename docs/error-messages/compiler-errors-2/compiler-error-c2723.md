---
title: Error de compilador Error C2723 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2723
dev_langs:
- C++
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01476218683205d0fb06e81847cfe9727b733158
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233789"
---
# <a name="compiler-error-c2723"></a>Error C2723 de Error del compilador
'function': el especificador 'specifier' no es válido en la definición de función  
  
 El especificador no puede aparecer con una definición de función fuera de una declaración de clase. El especificador `virtual` se puede especificar únicamente en una declaración de función miembro dentro de una declaración de clase.  
  
 El ejemplo siguiente genera el error C2723 y muestra cómo corregirlo:  
  
```  
// C2723.cpp  
struct X {  
   virtual void f();  
   virtual void g();  
};  
  
virtual void X::f() {}   // C2723  
  
// try the following line instead  
void X::g() {}  
```