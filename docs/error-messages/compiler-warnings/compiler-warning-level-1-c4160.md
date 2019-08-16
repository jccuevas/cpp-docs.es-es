---
title: Advertencia del compilador (nivel 1) C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: 988c1fcbe0826582dceaa527811c688711fd8906
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391847"
---
# <a name="compiler-warning-level-1-c4160"></a>Advertencia del compilador (nivel 1) C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>pragma (pop,...): no se encontró el identificador insertado anteriormente '*identificador*'

## <a name="remarks"></a>Comentarios

Una instrucción pragma en el código fuente intenta extraer un identificador que no se ha insertado. Para evitar esta advertencia, asegúrese de que el identificador que se vaya a extraer se haya insertado correctamente.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4160 y muestra cómo corregirlo:

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