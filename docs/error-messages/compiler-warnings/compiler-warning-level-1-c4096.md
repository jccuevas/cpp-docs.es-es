---
title: ADVERTENCIA del compilador (nivel 1) C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 4f5a45339673b57f946f206e1eaff0d23ec6fee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163941"
---
# <a name="compiler-warning-level-1-c4096"></a>ADVERTENCIA del compilador (nivel 1) C4096

' a ': la interfaz no es una interfaz COM; no se emitirá para IDL

Una definición de interfaz que puede haber diseñado como una interfaz COM no se ha definido como una interfaz COM y, por tanto, no se emitirá en el archivo IDL.

Vea [atributos de interfaz](../../windows/attributes/interface-attributes.md) para obtener una lista de atributos que indican que una interfaz es una interfaz com.

En el ejemplo siguiente se genera C4096:

```cpp
// C4096.cpp
// compile with: /W1 /LD
#include "windows.h"
[module(name="xx")];

// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct b : a
{
};   // C4096, remove coclass or uncomment object
```
