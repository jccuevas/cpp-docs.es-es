---
title: Error del compilador C2732 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 040fd73bcb69ef032d5c6150bb157337f34a2088
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079666"
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