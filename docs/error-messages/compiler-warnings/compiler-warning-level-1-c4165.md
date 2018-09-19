---
title: Compilador advertencia (nivel 1) C4165 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4165
dev_langs:
- C++
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c532ddee7a2066190c2f926ba7b1240c0418f6c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084931"
---
# <a name="compiler-warning-level-1-c4165"></a>Compilador advertencia (nivel 1) C4165

'HRESULT' se está convirtiendo en 'bool'; ¿está seguro de que desea realizar esta operación?

Cuando se usa un valor HRESULT en un [si](../../cpp/if-else-statement-cpp.md) instrucción, el valor HRESULT se convertirá en un [bool](../../cpp/bool-cpp.md) a menos que se pruebe explícitamente la variable como un valor HRESULT. De forma predeterminada, esta advertencia está desactivada.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4165

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```