---
title: Error del compilador C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: 98b43a2f3c0888fc385226cd80889b9911c84690
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227920"
---
# <a name="compiler-error-c2757"></a>Error del compilador C2757

'símbolo': ya existe un símbolo con este nombre y, por tanto, no se puede usar este nombre como un espacio de nombres

Ya se se usa un símbolo usado en la compilación actual como un identificador de espacio de nombres en un ensamblado de referencia.

El ejemplo siguiente genera C2757:

```
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

Y luego,

```
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
