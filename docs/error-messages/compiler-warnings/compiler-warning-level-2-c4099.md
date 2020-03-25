---
title: ADVERTENCIA del compilador (nivel 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 97ead14dc9771dc02ad722843ec9fe1a8056e3f6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174289"
---
# <a name="compiler-warning-level-2-c4099"></a>ADVERTENCIA del compilador (nivel 2) C4099

' Identifier ': el nombre de tipo que apareció por primera vez con ' objecttype1 ' se ha detectado ahora con ' objecttype2 '

Un objeto declarado como una estructura se define como una clase o un objeto declarado como una clase se define como una estructura. El compilador utiliza el tipo dado en la definición.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4099.

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```
