---
title: Error del compilador C3669
ms.date: 11/04/2016
f1_keywords:
- C3669
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
ms.openlocfilehash: 3b0ad3aa7395f5f423c8c36f547d4a0e2ad792c1
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777108"
---
# <a name="compiler-error-c3669"></a>Error del compilador C3669

'member': 'override' no se permite en constructores ni las funciones miembro estáticas en el especificador de invalidación

Se ha especificado incorrectamente un reemplazo. Para obtener más información, consulte [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3669.

```
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```