---
title: Especialización explícita de las plantillas de función
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: c9d77cef790bdd0a65651ffb7246e685175482b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179996"
---
# <a name="explicit-specialization-of-function-templates"></a>Especialización explícita de las plantillas de función

Con una plantilla de función, puede definir un comportamiento especial para un tipo específico si proporciona una especialización explícita (reemplazo) de la plantilla de función de ese tipo. Por ejemplo:

```cpp
template<> void MySwap(double a, double b);
```

Esta declaración permite definir una función diferente para las variables **dobles** . Al igual que las funciones que no son de plantilla, se aplican las conversiones de tipo estándar (como la promoción de una variable de tipo **float** a **Double**).

## <a name="example"></a>Ejemplo

```cpp
// explicit_specialization.cpp
template<class T> void f(T t)
{
};

// Explicit specialization of f with 'char' with the
// template argument explicitly specified:
//
template<> void f<char>(char c)
{
}

// Explicit specialization of f with 'double' with the
// template argument deduced:
//
template<> void f(double d)
{
}
int main()
{
}
```

## <a name="see-also"></a>Consulte también

[Plantillas de función](../cpp/function-templates.md)
