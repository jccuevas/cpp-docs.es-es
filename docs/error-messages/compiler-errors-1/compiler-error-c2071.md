---
title: Compilador Error C2071 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c62bb735a84b04bfb0c1addd5e3dd20a48a3eb33
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2071"></a>Error C2071 de Error del compilador
'identificador': clase de almacenamiento no válida  
  
 `identifier`se ha declarado con un válido [clase de almacenamiento](../../c-language/c-storage-classes.md). Este error puede producirse cuando se especifica más de una clase de almacenamiento para un identificador, o cuando la definición no es compatible con la declaración de clase de almacenamiento.  
  
 Para corregir este problema, comprender la clase de almacenamiento previsto del identificador, por ejemplo, `static` o `extern`y corrija la declaración debe coincidir.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C2071.  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C2071.  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```
