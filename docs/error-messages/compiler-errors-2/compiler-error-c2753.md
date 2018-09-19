---
title: Error del compilador C2753 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2753
dev_langs:
- C++
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 722176744dc614e54d7b25ffd75be679ef9e63dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060595"
---
# <a name="compiler-error-c2753"></a>Error del compilador C2753

'*plantilla*': la especialización parcial no puede coincidir con la lista de argumentos de plantilla principal

Si la lista de argumentos de plantilla coincide con la lista de parámetros, el compilador trata como la misma plantilla. No se permite definir dos veces la misma plantilla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2753 y muestra cómo corregirlo:

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```