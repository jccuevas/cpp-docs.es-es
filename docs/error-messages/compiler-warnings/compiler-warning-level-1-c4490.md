---
title: Compilador advertencia (nivel 1) C4490 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4490
dev_langs:
- C++
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d6bda2aaf729c2d4b8fb29dcbeaff428ed79d78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090872"
---
# <a name="compiler-warning-level-1-c4490"></a>Advertencia del compilador (nivel 1) C4490

'override': uso incorrecto del especificador de invalidación; 'function' no coincide con un método de clase ref base

Un especificador de invalidación se usó incorrectamente. Por ejemplo, no reemplaza una función de la interfaz, implementarla.

Para obtener más información, consulte [especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4490.

```
// C4490.cpp
// compile with: /clr /c /W1

interface struct IFace {
   void Test();
};

ref struct Class1 : public IFace {
   virtual void Test() override {}   // C4490
   // try the following line instead
   // virtual void Test() {}
};
```