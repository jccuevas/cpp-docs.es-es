---
title: Compilador advertencia (nivel 1) C4651 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b516ef86372901d00dd20d94ed10d5e361bbab8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099478"
---
# <a name="compiler-warning-level-1-c4651"></a>Advertencia del compilador (nivel 1) C4651

'definición de especificado para el encabezado precompilado pero no para la compilación actual

La definición se especificó cuando se generó el encabezado precompilado, pero no en esta compilación.

La definición se aplicará en el encabezado precompilado, pero no en el resto del código.

Si un encabezado precompilado se compiló con/DSYMBOL, el compilador genera esta advertencia si el /Yu no tiene/DSYMBOL.  Agregar/DSYMBOL a la línea de comandos /Yu resuelve esta advertencia.