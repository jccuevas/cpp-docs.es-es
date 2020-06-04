---
title: Error del compilador C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: 3d290bd2288f76d0ddefa2057e3e01c9edc3cbc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205327"
---
# <a name="compiler-error-c2461"></a>Error del compilador C2461

> '*Class*': faltan parámetros formales en la sintaxis del constructor

El constructor de la clase no especifica ningún parámetro formal. La declaración de un constructor debe especificar una lista de parámetros formales. La lista puede estar vacía.

Para corregir este problema, agregue un par de paréntesis después de la declaración de *clase*::**clase*.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo corregir C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```
