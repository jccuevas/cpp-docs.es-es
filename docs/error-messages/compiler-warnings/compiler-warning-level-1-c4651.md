---
title: Compilador advertencia (nivel 1) C4651 | Documentos de Microsoft
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
ms.openlocfilehash: 0015102a44b71f342b125532d20849590157ee0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283372"
---
# <a name="compiler-warning-level-1-c4651"></a>Advertencia del compilador (nivel 1) C4651
'definición de especificado para el encabezado precompilado pero no para la compilación actual  
  
 La definición se especificó cuando se generó el encabezado precompilado, pero no en esta compilación.  
  
 La definición se aplicará en el encabezado precompilado, pero no en el resto del código.  
  
 Si un encabezado precompilado se compiló con/DSYMBOL, el compilador generará esta advertencia si el /Yu no tiene/DSYMBOL.  Agregar/DSYMBOL a la línea de comandos de /Yu corrige esta advertencia.