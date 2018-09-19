---
title: Compilador advertencia (nivel 2) C4653 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4653
dev_langs:
- C++
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 376da24d4619eacc3e6b3defe8fdfc582800a898
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045983"
---
# <a name="compiler-warning-level-2-c4653"></a>Advertencia del compilador (nivel 2) C4653

opción del compilador 'opción' incoherente con el encabezado precompilado; omitirá la opción de línea de comandos actual

Una opción especificada con utilizar encabezado precompilado ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) era incoherente con las opciones especificadas cuando se creó el encabezado precompilado. Esta compilación usa la opción especificada cuando se creó el encabezado precompilado.

Esta advertencia puede producirse cuando un valor diferente para la opción Empaquetar estructuras ([/Zp](../../build/reference/zp-struct-member-alignment.md)) se ha especificado durante la compilación del encabezado precompilado.