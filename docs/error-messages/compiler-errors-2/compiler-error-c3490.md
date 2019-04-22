---
title: Error del compilador C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 1e6c3c502290e88feec89877de7ad791084401cf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023261"
---
# <a name="compiler-error-c3490"></a>Error del compilador C3490

'var' no se puede modificar porque se está accediendo a través de un objeto const.

Una expresión lambda que se declara en un método `const` no puede modificar los datos de miembro no mutable.

### <a name="to-correct-this-error"></a>Para corregir este error

- Elimine el modificador `const` de la declaración del método.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3490 porque modifica la variable miembro `_i` en un método `const` :

```
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se resuelve C3490 quitando el modificador `const` de la declaración del método:

```
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)