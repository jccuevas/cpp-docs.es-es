---
title: Error del compilador C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: e8f82ed4ce8ad77a22961a42c8e9a256e6f647db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368037"
---
# <a name="compiler-error-c2461"></a>Error del compilador C2461

> '*clase*': sintaxis del constructor faltan parámetros formales

El constructor de la clase no especifica ningún parámetro formal. La declaración de un constructor debe especificar una lista de parámetros formales. La lista puede estar vacía.

Para corregir este problema, agregue un par de paréntesis después de la declaración de *clase*:: **clase*.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo corregir C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```