---
title: Compilador advertencia (nivel 3) C4641 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4641
dev_langs:
- C++
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f44e94868f6a7b379fb1a2f75bbd28ce011b54c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112114"
---
# <a name="compiler-warning-level-3-c4641"></a>Advertencia del compilador (nivel 3) C4641

el comentario del documento XML tiene una referencia cruzada ambigua

El compilador no pudo resolver una referencia de forma inequívoca. Para resolver esta advertencia, especifique la información de parámetros necesaria para que la referencia no sean ambiguos.

Para obtener más información, consulta [XML Documentation](../../ide/xml-documentation-visual-cpp.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4641.

```
// C4641.cpp
// compile with: /W3 /doc /clr /c

/// <see cref="f" />   // C4641
// try the following line instead
// /// <see cref="f(int)" />
public ref class GR {
public:
   void f( int ) {}
   void f( char ) {}
};
```