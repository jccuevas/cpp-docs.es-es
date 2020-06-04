---
title: Advertencia del compilador (nivel 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: bc8131665c970c3b86bb1e84e39636ae8f93897b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199547"
---
# <a name="compiler-warning-level-1-c4651"></a>Advertencia del compilador (nivel 1) C4651

' Definition ' especificado para el encabezado precompilado, pero no para la compilación actual

La definición se especificó cuando se generó el encabezado precompilado, pero no en esta compilación.

La definición estará en vigor dentro del encabezado precompilado, pero no en el resto del código.

Si un encabezado precompilado se compiló con/DSYMBOL, el compilador generará esta advertencia si/Yu compile no tiene/DSYMBOL.  Al agregar/DSYMBOL a la línea de comandos/Yu se resuelve esta advertencia.
