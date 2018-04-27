---
title: vector&lt;bool&gt;::reference (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vector/vector<bool>::reference
dev_langs:
- C++
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf26443710d57352e3d7840f9b03455c2932b0fb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

|Función miembro|Descripción|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|Invierte el valor booleano de un elemento vector.|
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|Proporciona una conversión implícita de `vector<bool>::reference` en `bool`.|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|Asigna un valor booleano a un bit o asigna el valor contenido en un elemento al que se hace referencia a un bit.|

## <a name="requirements"></a>Requisitos

**Encabezado**: \<vector>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<vector>](../standard-library/vector.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
