---
title: Error del compilador C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 4d1cd510cda9957ced1d9dd5fd8fea267f39220d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300562"
---
# <a name="compiler-error-c3366"></a>Error del compilador C3366

'variable': los miembros de datos estáticos de administran o WinRTtypes deben estar definidos dentro de la definición de clase

Ha intentado hacer referencia a un miembro estático de una clase o interfaz .NET o WinRT fuera de la definición de esa clase o interfaz.

El compilador necesita conocer la definición completa de la clase (para emitir los metadatos después de un paso) y requiere que los miembros de datos estáticos se inicialicen en la clase.

Por ejemplo, en el ejemplo siguiente se genera el error C3366 y se muestra cómo corregirlo:

```
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
