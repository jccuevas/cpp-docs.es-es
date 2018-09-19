---
title: Error del compilador C3298 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3298
dev_langs:
- C++
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06296fed3f33b56cb53cf3bc4531205638f0a204
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053696"
---
# <a name="compiler-error-c3298"></a>Error del compilador C3298

'restricción_1': no se puede usar 'restricción_2' como restricción porque 'restricción_2' tiene la restricción de referencia y 'restricción_1' tiene la restricción de valor.

No se pueden especificar características que se excluyen mutuamente para una restricción. Por ejemplo, un parámetro de tipo genérico no se puede restringir a un tipo de valor y a un tipo de referencia.

Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3298.

```
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```