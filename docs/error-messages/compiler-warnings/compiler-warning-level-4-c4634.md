---
title: Del compilador (nivel 4) de la advertencia C4634 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4634
dev_langs:
- C++
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fe89eaffda80ab40efedc4facf75929d07a7537
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034920"
---
# <a name="compiler-warning-level-4-c4634"></a>Advertencia del compilador (nivel 4) C4634

Comentario del documento XML: no se puede aplicar: motivo

No se pueden aplicar etiquetas de documentación XML a todas las construcciones C++.  Por ejemplo, no puede agregar un comentario de documentación a un espacio de nombres o plantilla.

Para obtener más información, consulta [XML Documentation](../../ide/xml-documentation-visual-cpp.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4634.

```
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4634.

```
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```