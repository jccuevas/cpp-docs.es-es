---
title: Error del compilador C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 5a3d9052775a5e1cbedfd58ccaaf0ff039a8475d
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693441"
---
# <a name="compiler-error-c2316"></a>Error del compilador C2316

> '*class_type*': no se puede detectar porque el destructor o constructor de copia es inaccesibles o eliminados

Se detectó una excepción por valor o por referencia, pero el constructor de copias, el operador de asignación, o ambos son inaccesibles.

## <a name="remarks"></a>Comentarios

Cambios de conformidad en Visual Studio 2015 realizan a este error se aplican a instrucciones catch incorrecta de excepciones de MFC derivadas de `CException`. Dado que `CException` tiene un constructor de copias privado heredado, la clase y sus derivados no se puede copiar y no se puede pasar por valor, lo que también significa que no se puede detectar por valor. Detecte las instrucciones que detectan excepciones de MFC mediante el valor que previamente se llevó a las excepciones no detectadas en tiempo de ejecución. Ahora el compilador identifica esta situación correctamente y notifica el error C2316. Para corregir este problema, se recomienda utilizar las macros TRY/CATCH de MFC en lugar de escribir sus propios controladores de excepciones. Si eso no resulta adecuado para el código, detectar las excepciones de MFC por referencia en su lugar.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2316 y muestra cómo corregirlo:

```cpp
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&) {}
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b)    // C2316
    {
        printf_s("Caught an exception!\n");
    }
}
```
