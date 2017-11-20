---
title: Bloques | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 18d04884bacf2cbc03fd68c8ec0489595eb0f4d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="blocks"></a>Bloques
Una secuencia de declaraciones, definiciones e instrucciones delimitada por llaves (**{ }**) se denomina "bloque". Hay dos tipos de bloques en C. La "instrucción compuesta", una instrucción compuesta de una o más instrucciones (vea [La instrucción compuesta](../c-language/compound-statement-c.md)), es un tipo de bloque. El otro, la “definición de función”, consta de una instrucción compuesta (el cuerpo de la función) más el “encabezado” asociado de la función (el nombre de la función, el tipo de valor devuelto y los parámetros formales). De un bloque ubicado dentro de otros bloques se dice que está “anidado”.  
  
 Observe que aunque todas las instrucciones compuestas se encuentran entre llaves, no todo lo que hay dentro de las llaves constituye una instrucción compuesta. Por ejemplo, aunque las especificaciones de elementos de matriz, estructura o enumeración pueden aparecer entre llaves, no son instrucciones compuestas.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de código fuente y programas origen](../c-language/source-files-and-source-programs.md)