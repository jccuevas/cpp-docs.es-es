---
title: Advertencia del compilador (nivel 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: e3cda7ed70963508d7663c6c12b2b98ac64db204
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400921"
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