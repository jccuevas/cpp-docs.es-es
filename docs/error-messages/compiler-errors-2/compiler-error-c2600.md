---
title: Compilador Error C2600 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13b4cdf15dca9b3978f8c7855a5f1b07cc86f0b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230954"
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