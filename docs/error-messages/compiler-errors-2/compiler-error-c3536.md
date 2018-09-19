---
title: Error del compilador C3536 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7585a75ebe9733c228756e92d8e5ae57699aca27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088584"
---
# <a name="compiler-error-c3536"></a>Error del compilador C3536

'símbolo': no se puede usar antes de inicializarse

No se puede usar el símbolo indicado antes de inicializarse. En la práctica, esto significa que una variable no se puede usar para inicializarse a sí misma.

### <a name="to-correct-this-error"></a>Para corregir este error

1. No se inicialice una variable consigo misma.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3536 porque cada variable se inicializa con sí mismo.

```
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)