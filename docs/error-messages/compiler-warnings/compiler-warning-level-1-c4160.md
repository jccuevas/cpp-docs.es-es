---
title: Compilador advertencia (nivel 1) C4160 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4160
dev_langs:
- C++
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c62bf021065870f2ddd64cd7ee08cc00504cf7bd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219680"
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