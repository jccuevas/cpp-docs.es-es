---
title: Error del compilador C2555
description: Referencia para el error del compilador C2555 de Visual Studio C++.
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: fe0e6379e783387506e6098c9b14a047baa8e6c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374171"
---
# <a name="compiler-error-c2555"></a>Error del compilador C2555

> '*class1*::*function1*': reemplazando el tipo de retorno de función virtual difiere y no es covariante de '*class2*::*function2*'

Una función virtual y una función de reemplazo derivada tienen listas de parámetros idénticas pero tipos de valor devuelto diferentes.

## <a name="remarks"></a>Observaciones

En C++, una función de reemplazo en una clase derivada no puede diferir solo por el tipo de valor devuelto de una función virtual en una clase base.

Hay una excepción a esta regla para ciertos tipos de valor devuelto. Cuando una clase derivada reemplaza una clase base pública, puede devolver un puntero o una referencia a la clase derivada en lugar de un puntero o referencia de clase base. Estos tipos de valor devuelto se denominan *covariante,* porque varían junto con el tipo. Esta excepción de regla no permite tipos covariante de referencia a puntero o puntero a puntero.

Una forma de resolver el error es devolver el mismo tipo que la clase base. A continuación, convierta el valor devuelto después de llamar a la función virtual. Otro es también cambiar la lista de parámetros, para hacer que la función miembro de clase derivada una sobrecarga en lugar de una invalidación.

## <a name="examples"></a>Ejemplos

Es posible que vea este **`/clr`** error si compila con . Por ejemplo, el c+ equivalente a la siguiente declaración de C-:

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

El ejemplo siguiente genera C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```

Para solucionarlo, cambie el `Y::func` `void`tipo de valor devuelto de a .
