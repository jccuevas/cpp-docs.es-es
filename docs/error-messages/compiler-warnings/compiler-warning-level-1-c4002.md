---
title: Del compilador (nivel 1) de la advertencia C4002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4002
dev_langs:
- C++
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3b3d51b4408e79236993d49f7ceba5fc9537b6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050143"
---
# <a name="compiler-warning-level-1-c4002"></a>Advertencia del compilador (nivel 1) C4002

hay demasiados parámetros reales para la macro 'identifier'

El número de parámetros reales de la macro supera el número de parámetros formales de la definición de macro. El preprocesador obtiene los parámetros adicionales pero los omite durante la expansión de macro.

La advertencia C4002 puede aparecer al usar [Variadic Macros](../../preprocessor/variadic-macros.md)de manera incorrecta.

El ejemplo siguiente genera la advertencia C4002:

```
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio. NET 2003: ya no se acepta el uso de comas adicionales en la macro.

El compilador ya no aceptará comas adicionales en una macro. Para que el código sea válido en las versiones de Visual Studio .NET 2003 y de Visual Studio .NET de Visual C++, quite las comas adicionales.

```
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```