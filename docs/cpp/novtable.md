---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: d101e73f2f8d476c50b1b80b8daa7994151d43af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177838"
---
# <a name="novtable"></a>novtable

**Específicos de Microsoft**

Se trata de un atributo extendido **__declspec** .

Esta forma de **__declspec** se puede aplicar a cualquier declaración de clase, pero solo debe aplicarse a las clases de interfaz puras, es decir, las clases de las que nunca se crearán instancias por sí mismas. El **__declspec** impide que el compilador genere código para inicializar vfptr en los constructores y en el destructor de la clase. En muchos casos, esto quita las únicas referencias a la vtable asociadas a la clase y, en consecuencia, el vinculador la quita. El uso de esta forma de **__declspec** puede producir una reducción significativa del tamaño del código.

Si intenta crear una instancia de una clase marcada con **novtable** y, a continuación, tiene acceso a un miembro de clase, recibirá una infracción de acceso (AV).

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

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
