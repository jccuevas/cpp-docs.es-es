---
title: Error del compilador C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 95344b5ef675f566f433dfeaed9dee5c38ef77d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303352"
---
# <a name="compiler-error-c2071"></a>Error del compilador C2071

'identificador': clase de almacenamiento no válida

`identifier` se ha declarado con un no válido [clase de almacenamiento](../../c-language/c-storage-classes.md). Este error puede producirse cuando se especifica más de una clase de almacenamiento para un identificador, o cuando la definición no es compatible con la declaración de clase de almacenamiento.

Para corregir este problema, averigüe la clase de almacenamiento previsto del identificador, por ejemplo, `static` o `extern`y corrija la declaración para hacer coincidir.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2071.

```
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2071.

```
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```