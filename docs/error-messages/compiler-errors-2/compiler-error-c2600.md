---
title: Compilador Error C2600 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 1fe5383e17212b21c11394c6b987e92aacbe637e
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2600"></a>C2600 de Error del compilador
'función': no se puede definir una función miembro especial generada por el compilador (se debe declarar primero en la clase)  
  
 Antes de que se puedan definir funciones miembro, como constructores o destructores, para una clase, se deben declarar en la clase. Si no se declaran en la clase, el compilador puede generar constructores y destructores predeterminados (lo que se conoce como funciones miembro especiales). Sin embargo, si define una de estas funciones sin una declaración coincidente en la clase, el compilador detecta un conflicto.  
  
 Para corregir este error, en la declaración de clase, declare cada función miembro que defina fuera de la declaración de clase.  
  
 El código siguiente genera el error C2600:  
  
```  
// C2600.cpp  
// compile with: /c  
class C {};  
C::~C() {}   // C2600  
  
class D {  
   D::~D();  
};  
  
D::~D() {}  
```
