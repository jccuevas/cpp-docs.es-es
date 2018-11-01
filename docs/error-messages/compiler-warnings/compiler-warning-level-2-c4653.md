---
title: Advertencia del compilador (nivel 2) C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 664b1b3ec732c323d0074310902890cdd6eca9a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588605"
---
# <a name="compiler-warning-level-2-c4653"></a>Advertencia del compilador (nivel 2) C4653

opción del compilador 'opción' incoherente con el encabezado precompilado; omitirá la opción de línea de comandos actual

Una opción especificada con utilizar encabezado precompilado ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) era incoherente con las opciones especificadas cuando se creó el encabezado precompilado. Esta compilación usa la opción especificada cuando se creó el encabezado precompilado.

Esta advertencia puede producirse cuando un valor diferente para la opción Empaquetar estructuras ([/Zp](../../build/reference/zp-struct-member-alignment.md)) se ha especificado durante la compilación del encabezado precompilado.