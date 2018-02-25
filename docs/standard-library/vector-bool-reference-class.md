---
title: vector&lt;bool&gt;::reference (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vector/vector<bool>::reference
dev_langs:
- C++
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 56101a717c56a3999ad32648de8f9ae75d7439d0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference (Clase)
La clase `vector<bool>::reference` es una clase de proxy proporcionada por [vector\<bool> (Clase)](../standard-library/vector-bool-class.md) para simular `bool&`.  
  
## <a name="remarks"></a>Comentarios  
 Se requiere una referencia simulada porque C++ no permite de forma nativa referencias directas a bits. `vector<bool>` solo utiliza un bit por elemento, al que se puede hacer referencia mediante esta clase proxy. Sin embargo, la simulación de referencia no se completa porque algunas asignaciones no son válidas. Por ejemplo, dado que no se puede tomar la dirección del objeto `vector<bool>::reference`, el siguiente código, que usa [vector\<bool>::operator&#91;&#93;](http://msdn.microsoft.com/Library/97738633-690d-4069-b2d9-8c54104fbfdd), no es correcto:  
  
```cpp  
vector<bool> vb;  
// ...  
bool* pb = &vb[1]; // conversion error - do not use  
bool& refb = vb[1];   // conversion error - do not use  
```  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[flip](../standard-library/vector-bool-reference-flip.md)|Invierte el valor booleano de un elemento vector.|  
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|Proporciona una conversión implícita de `vector<bool>::reference` en `bool`.|  
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|Asigna un valor booleano a un bit o asigna el valor contenido en un elemento al que se hace referencia a un bit.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: \<vector>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<vector>](../standard-library/vector.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)

