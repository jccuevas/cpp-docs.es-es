---
title: Advertencia del compilador (nivel 1) C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: 8eb53d3f00c717df0e657ede3de6dd71d4a0bb47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176174"
---
# <a name="compiler-warning-level-1-c4160"></a>Advertencia del compilador (nivel 1) C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>pragma (pop,...): no se encontró el identificador insertado anteriormente '*Identifier*'

## <a name="remarks"></a>Observaciones

Una instrucción pragma en el código fuente intenta extraer un identificador que no se ha insertado. Para evitar esta advertencia, asegúrese de que el identificador que se vaya a extraer se haya insertado correctamente.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4160 y se muestra cómo corregirlo:

```cpp
// C4160.cpp
// compile with: /W1
#pragma pack(push)

#pragma pack(pop, id)   // C4160
// use identifier when pushing to resolve the warning
// #pragma pack(push, id)

int main() {
}
```
