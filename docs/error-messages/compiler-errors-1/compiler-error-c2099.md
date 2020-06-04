---
title: Error del compilador C2099
ms.date: 11/04/2016
f1_keywords:
- C2099
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
ms.openlocfilehash: e9fb7739111d13a585579455ed97cecaca3266e4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301943"
---
# <a name="compiler-error-c2099"></a>Error del compilador C2099

el inicializador no es una constante

Este error solo lo emite el compilador de C y únicamente se genera para variables no automáticas.  El compilador inicializa variables no automáticas al inicio del programa y los valores con los que se inicializan deben ser constantes.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2099.

```c
// C2099.c
int j;
int *p;
j = *p;   // C2099 *p is not a constant
```

## <a name="example"></a>Ejemplo

El error C2099 también puede producirse porque el compilador no puede efectuar el plegamiento constante sobre una expresión en **/fp:strict** , porque la configuración del entorno de precisión de punto flotante (vea [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md) para obtener más información) puede ser distinta en la compilación y en el tiempo de ejecución.

Cuando falla el plegamiento constante, el compilador invoca una inicialización dinámica, que no se permite en C.

Para resolver este error, compile el módulo como archivo .cpp o simplifique la expresión.

Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md).

El ejemplo siguiente genera la advertencia C2099.

```c
// C2099_2.c
// compile with: /fp:strict /c
float X = 2.0 - 1.0;   // C2099
float X2 = 1.0;   // OK
```
