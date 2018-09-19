---
title: Compilador advertencia (nivel 4) C4268 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a8152ef690b9ded63b91b2b6e6f1da6dc2524
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063715"
---
# <a name="compiler-warning-level-4-c4268"></a>Advertencia del compilador (nivel 4) C4268

'identifier': los datos estáticos/globales 'const' inicializados con el constructor de predeterminado generado por compilador rellenan el objeto con ceros

Un **const** instancia global o estática de una clase no trivial se inicializa con un constructor predeterminado generado por el compilador.

## <a name="example"></a>Ejemplo

```
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Como esta instancia de la clase es **const**, el valor de `m_data` no se puede cambiar.