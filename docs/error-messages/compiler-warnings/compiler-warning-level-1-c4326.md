---
title: Compilador advertencia (nivel 1) C4326 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4326
dev_langs:
- C++
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cee18a9ccc807370cf2fb40748939f211a4ba52f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211009"
---
# <a name="compiler-warning-level-1-c4326"></a>Advertencia del compilador (nivel 1) C4326

> tipo de valor devuelto '*función*'debe ser'*type1*'en lugar de'*type2*'

## <a name="remarks"></a>Comentarios

Una función devuelve un tipo distinto *type1*. Por ejemplo, mediante [/Za](../../build/reference/za-ze-disable-language-extensions.md), **principal** no devolvió un **int**.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4326 y muestra cómo corregirlo:

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```