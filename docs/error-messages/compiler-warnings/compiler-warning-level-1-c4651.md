---
title: Compilador advertencia (nivel 1) C4651 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4651
dev_langs: C++
helpviewer_keywords: C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dce099d657341ebc957c95ab0cd14f508f9e36ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4651"></a>Advertencia del compilador (nivel 1) C4651
'definición de especificado para el encabezado precompilado pero no para la compilación actual  
  
 La definición se especificó cuando se generó el encabezado precompilado, pero no en esta compilación.  
  
 La definición se aplicará en el encabezado precompilado, pero no en el resto del código.  
  
 Si un encabezado precompilado se compiló con/DSYMBOL, el compilador generará esta advertencia si el /Yu no tiene/DSYMBOL.  Agregar/DSYMBOL a la línea de comandos de /Yu corrige esta advertencia.