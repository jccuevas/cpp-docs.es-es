---
title: Error del compilador C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 2676a32cee487595a2241359496ae9b0380126b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329197"
---
# <a name="compiler-error-c2844"></a>Error del compilador C2844

'member': no puede ser un miembro de interfaz 'interface'

Un [clase interface](../../extensions/interface-class-cpp-component-extensions.md) no puede contener un miembro de datos a menos que también es una propiedad.

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
