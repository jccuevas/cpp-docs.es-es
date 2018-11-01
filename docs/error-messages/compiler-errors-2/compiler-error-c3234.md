---
title: Error del compilador C3234
ms.date: 11/04/2016
f1_keywords:
- C3234
helpviewer_keywords:
- C3234
ms.assetid: ebefc15a-e40d-424b-a3dd-d7e185d0ed7b
ms.openlocfilehash: fd6e918c115ed121dda5d589a62b1a94d14184a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477602"
---
# <a name="compiler-error-c3234"></a>Error del compilador C3234

una clase genérica no puede derivar de un parámetro de tipo genérico

Una clase genérica no puede heredar de un parámetro de tipo genérico.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3234.

```
// C3234.cpp
// compile with: /clr /c
generic <class T>
public ref class C : T {};   // C3234
// try the following line instead
// public ref class C {};
```