---
title: Bloques
ms.date: 11/04/2016
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
ms.openlocfilehash: 4f308864e6e85f74e40d9c9df200a0254fea366a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152630"
---
# <a name="blocks"></a>Bloques

Una secuencia de declaraciones, definiciones e instrucciones delimitada por llaves (**{ }**) se denomina "bloque". Hay dos tipos de bloques en C. La "instrucción compuesta", una instrucción compuesta de una o más instrucciones (vea [La instrucción compuesta](../c-language/compound-statement-c.md)), es un tipo de bloque. El otro, la “definición de función”, consta de una instrucción compuesta (el cuerpo de la función) más el “encabezado” asociado de la función (el nombre de la función, el tipo de valor devuelto y los parámetros formales). De un bloque ubicado dentro de otros bloques se dice que está “anidado”.

Observe que aunque todas las instrucciones compuestas se encuentran entre llaves, no todo lo que hay dentro de las llaves constituye una instrucción compuesta. Por ejemplo, aunque las especificaciones de elementos de matriz, estructura o enumeración pueden aparecer entre llaves, no son instrucciones compuestas.

## <a name="see-also"></a>Vea también

[Archivos de código fuente y programas origen](../c-language/source-files-and-source-programs.md)
