---
title: Error del compilador C2099 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2099
dev_langs:
- C++
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fcbefa4d8fb9d5503f28cf3bf39cafc6b05a225
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116833"
---
# <a name="compiler-error-c2099"></a>Error del compilador C2099

el inicializador no es una constante

Este error solo lo emite el compilador de C y únicamente se genera para variables no automáticas.  El compilador inicializa variables no automáticas al inicio del programa y los valores con los que se inicializan deben ser constantes.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2099.

```
// C2099.c
int j;
int *p;
j = *p;   // C2099 *p is not a constant
```

## <a name="example"></a>Ejemplo

El error C2099 también puede producirse porque el compilador no puede efectuar el plegamiento constante sobre una expresión en **/fp:strict** , porque la configuración del entorno de precisión de punto flotante (vea [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md) para obtener más información) puede ser distinta en la compilación y en el tiempo de ejecución.

Cuando falla el plegamiento constante, el compilador invoca una inicialización dinámica, que no se permite en C.

Para resolver este error, compile el módulo como archivo .cpp o simplifique la expresión.

Para obtener más información, consulte [/fp (Specify Floating-Point Behavior)](../../build/reference/fp-specify-floating-point-behavior.md).

El ejemplo siguiente genera la advertencia C2099.

```
// C2099_2.c
// compile with: /fp:strict /c
float X = 2.0 - 1.0;   // C2099
float X2 = 1.0;   // OK
```