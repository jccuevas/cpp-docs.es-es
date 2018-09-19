---
title: Compilador advertencia (nivel 1) C4042 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bef2071cf31123b5b172df2651c0d6a6d87d4fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067483"
---
# <a name="compiler-warning-level-1-c4042"></a>Compilador advertencia (nivel 1) C4042

'identifier': tiene la clase de almacenamiento incorrecta

La clase de almacenamiento especificada no se puede usar con este identificador en este contexto. El compilador usa la clase de almacenamiento predeterminada en su lugar:

- `extern`, si *identificador* es una función.

- **Auto**si *identificador* es un parámetro formal o una variable local.

- La clase sin almacenamiento si *identificador* es una variable global.

Esta advertencia puede deberse a que se especifica una clase de almacenamiento distinto **registrar** en una declaración de parámetro.

El ejemplo siguiente genera C4042

```
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```