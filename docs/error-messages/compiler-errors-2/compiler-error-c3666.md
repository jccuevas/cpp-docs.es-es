---
title: Error del compilador C3666
ms.date: 11/04/2016
f1_keywords:
- C3666
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
ms.openlocfilehash: edca117da585fee731041d696e05af1baf6d3e5c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776540"
---
# <a name="compiler-error-c3666"></a>Error del compilador C3666

'constructor': 'keyword' no se permite en un constructor de especificador de invalidación

Se usó un especificador de invalidación en un constructor, y que no se permite. Para obtener más información, consulte [especificadores de invalidación](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3666.

```
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```