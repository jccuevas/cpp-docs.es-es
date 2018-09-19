---
title: novtable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- novtable_cpp
dev_langs:
- C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2de25452d708545481bdc4a65cab998930b2778e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068440"
---
# <a name="novtable"></a>novtable

## <a name="microsoft-specific"></a>Específicos de Microsoft

Se trata de un **__declspec** atributo extendido.

Esta forma de **__declspec** se pueden aplicar a cualquier declaración de clase, pero solo se debe aplicar a clases de interfaz puras, es decir, las clases que nunca se crearán instancias por sí solos. El **__declspec** evita que el compilador genere código para inicializar vfptr en los constructores y el destructor de la clase. En muchos casos, esto quita las únicas referencias a la vtable asociadas a la clase y, en consecuencia, el vinculador la quita. Uso de esta forma de **__declspec** puede dar lugar a una reducción significativa del tamaño del código.

Si se intenta crear una instancia de una clase marcada con **novtable** y, a continuación, obtener acceso a un miembro de clase, recibirá una infracción de acceso (AV).

## <a name="example"></a>Ejemplo

```cpp
// novtable.cpp
#include <stdio.h>

struct __declspec(novtable) X {
   virtual void mf();
};

struct Y : public X {
   void mf() {
      printf_s("In Y\n");
   }
};

int main() {
   // X *pX = new X();
   // pX->mf();   // Causes a runtime access violation.

   Y *pY = new Y();
   pY->mf();
}
```

```Output
In Y
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)