---
title: Compilador advertencia (nivel 3) C4373 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4373
dev_langs:
- C++
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fda965fe80fc26731cde7be5a71540e6454a7360
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4373"></a>Advertencia del compilador (nivel 3) C4373

> '*función*': los reemplazos de funciones virtuales*función_base*', las versiones anteriores del compilador no se reemplazaron cuando los parámetros solo se diferenciaban en los calificadores const y volatile

## <a name="remarks"></a>Comentarios

La aplicación contiene un método en una clase derivada que reemplaza un método virtual en una clase base, y los parámetros en el método de reemplazo difieren solo en un calificador [const](../../cpp/const-cpp.md) o [volatile](../../cpp/volatile-cpp.md) de los parámetros del método virtual. Esto significa que el compilador debe enlazar una referencia a función con el método en la clase derivada o base.

Las versiones del compilador anteriores a Visual Studio 2008 enlazan la función con el método de la clase base, a continuación, emiten un mensaje de advertencia. Las versiones posteriores del compilador omiten el `const` o `volatile` calificador, enlazar la función con el método de la clase derivada, a continuación, emitir advertencia **C4373**. Este último comportamiento cumple con el estándar de C++.

## <a name="example"></a>Ejemplo

El siguiente código de ejemplo genera la advertencia C4373. Para resolver este problema, puede establecer la invalidación de usar el mismo calificador CV como la función miembro base, o si no se pretendía crear una invalidación, puede conceder a la función en la clase derivada un nombre diferente.

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

void main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```