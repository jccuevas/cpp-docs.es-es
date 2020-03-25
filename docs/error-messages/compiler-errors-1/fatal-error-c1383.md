---
title: Error irrecuperable C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 6c0be830cb56b760f1397ea2b2f81b42a87e9ba6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203091"
---
# <a name="fatal-error-c1383"></a>Error irrecuperable C1383

la opción /GL del compilador es incompatible con la versión instalada de Common Language Runtime

El error C1383 se genera si utiliza una versión anterior de Common Language Runtime con un compilador más reciente y cuando se compila con **/clr** y **/GL.**

Para solucionarlo, no utilice **/GL** con **/clr** o instale la versión de Common Language Runtime que se distribuía con su compilador.

Para obtener más información, consulte [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) y [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md).
