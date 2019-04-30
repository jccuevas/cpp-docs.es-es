---
title: Error del compilador C2316
ms.date: 11/04/2016
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 53e7743ec0d84451feb1dc1cd8849439aa142336
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345723"
---
# <a name="compiler-error-c2316"></a>Error del compilador C2316

> '*excepción*': no se puede detectar porque el destructor o constructor de copia es inaccesible

Se detectó una excepción por valor o por referencia, pero no se ha podido obtener acceso al constructor de copias o al operador de asignación.

Este código se aceptaba en versiones de Visual C++ antes de Visual Studio 2003, pero ahora produce un error.

Cambios de conformidad en Visual Studio 2015 realizan a este error se aplican a instrucciones catch incorrecta de excepciones de MFC derivadas de `CException`. Dado que `CException` tiene un constructor de copias privado heredado, la clase y sus derivados se no se puede copiar y no se puede pasar por valor, lo que también significa que no se puede detectar por valor. Detectar las instrucciones que detectan excepciones de MFC mediante el valor que previamente se llevó a las excepciones no detectadas en tiempo de ejecución, pero ahora el compilador identifica correctamente esta situación y el error C2316 de informes. Para corregir este problema, se recomienda que usar las macros TRY/CATCH de MFC en lugar de escriben sus propios controladores de excepciones, pero si eso no resulta adecuado para el código, detectar las excepciones de MFC por referencia en su lugar.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2316:

```
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

extern "C" int printf_s(const char*, ...);

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&)
    {
    }
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
    catch (B b) {   // C2316
        printf_s("Caught an exception!\n");
    }
}
```