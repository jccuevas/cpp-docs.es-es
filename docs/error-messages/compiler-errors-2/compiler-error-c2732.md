---
title: Error del compilador C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 820a620b7e4414123c56433f84536393834f6fd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585372"
---
# <a name="compiler-error-c2732"></a>Error del compilador C2732

la especificación de vinculación se contradice con la especificación anterior para 'function'

La función ya se ha declarado con otro especificador de vinculación.

Este error puede deberse a archivos de inclusión con otros especificadores de vinculación.

Para corregir este error, cambie las instrucciones `extern` para que las vinculaciones coincidan. En concreto, no incluya directivas `#include` en bloques `extern "C"`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2732:

```
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```