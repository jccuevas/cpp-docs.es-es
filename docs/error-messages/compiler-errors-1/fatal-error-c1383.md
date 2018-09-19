---
title: Error irrecuperable C1383 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98f6fe881b2cdc46d4d2848d6faf850381f54c7b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062194"
---
# <a name="fatal-error-c1383"></a>Error irrecuperable C1383

la opción /GL del compilador es incompatible con la versión instalada de Common Language Runtime

El error C1383 se genera si utiliza una versión anterior de Common Language Runtime con un compilador más reciente y cuando se compila con **/clr** y **/GL.**

Para solucionarlo, no utilice **/GL** con **/clr** o instale la versión de Common Language Runtime que se distribuía con su compilador.

Para obtener más información, consulte [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) y [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md).