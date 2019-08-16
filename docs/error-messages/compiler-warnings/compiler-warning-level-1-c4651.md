---
title: Advertencia del compilador (nivel 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: 01e2472a547e73eda5fcc56952949a0d9611029f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393524"
---
# <a name="compiler-warning-level-1-c4651"></a>Advertencia del compilador (nivel 1) C4651

'definición de especificado para el encabezado precompilado pero no para la compilación actual

La definición se especificó cuando se generó el encabezado precompilado, pero no en esta compilación.

La definición se aplicará en el encabezado precompilado, pero no en el resto del código.

Si un encabezado precompilado se compiló con/DSYMBOL, el compilador genera esta advertencia si el /Yu no tiene/DSYMBOL.  Agregar/DSYMBOL a la línea de comandos /Yu resuelve esta advertencia.