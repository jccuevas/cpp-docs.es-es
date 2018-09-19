---
title: Compilador advertencia (nivel 4) C4207 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4207
dev_langs:
- C++
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5aa7f364eb8f60d680dde4c252b9c84e258cda0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068837"
---
# <a name="compiler-warning-level-4-c4207"></a>Advertencia del compilador (nivel 4) C4207

extensión no estándar utilizada: ampliar el formulario de inicializador

Con las extensiones de Microsoft (/Ze), se puede inicializar una matriz sin tamaño de `char` mediante una cadena entre llaves.

## <a name="example"></a>Ejemplo

```
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

Inicializaciones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).