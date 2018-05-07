---
title: Error del compilador C2461 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47aee3122dad3e875cf58d5a41bcadda297e1463
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2461"></a>Error del compilador C2461
  
> '*clase*': sintaxis del constructor faltan parámetros formales  
  
 El constructor de la clase no especifica ningún parámetro formal. La declaración de un constructor debe especificar una lista de parámetros formales. La lista puede estar vacía.  
  
Para corregir este problema, agregue un par de paréntesis después de la declaración de *clase*:: **clase*.  
  
## <a name="example"></a>Ejemplo  
  
El ejemplo siguiente muestra cómo corregir C2461:  
  
```cpp  
// C2461.cpp  
// compile with: /c  
class C {  
   C::C;     // C2461  
   C::C();   // OK  
};  
```