---
title: Error del compilador C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 8af9f42be279f728f72fc6968aeba98ee5d2474a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462717"
---
# <a name="compiler-error-c2844"></a>Error del compilador C2844

'member': no puede ser un miembro de interfaz 'interface'

Un [clase interface](../../windows/interface-class-cpp-component-extensions.md) no puede contener un miembro de datos a menos que también es una propiedad.

Algo distinto de una propiedad o función miembro no se permite en una interfaz. Además, no se permiten constructores, destructores y operadores.

El ejemplo siguiente genera C2844:

```
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
