---
title: Definir una regla | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8a5cb7a0285f7abf8bcf476141451eae1b10f85
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705580"
---
# <a name="defining-a-rule"></a>Definir una regla

El *fromext* representa la extensión de un archivo dependiente, y *toext* representa la extensión de un archivo de destino.

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>Comentarios

Las extensiones no distinguen mayúsculas de minúsculas. Pueden llamar a macros para representar *fromext* y *toext*; se expanden las macros durante el preprocesamiento. El punto (.) anterior *fromext* debe aparecer al principio de la línea. Los dos puntos (:) está precedido por cero o más espacios o tabulaciones. Puede ser seguido de sólo espacios o tabulaciones, un punto y coma (;) para especificar un comando, un signo de número (#) para especificar un comentario o un carácter de nueva línea. No se permiten otras espacios en blanco. Los comandos se especifican como se muestra en bloques de descripción.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Rutas de búsqueda en reglas](../build/search-paths-in-rules.md)

## <a name="see-also"></a>Vea también

[Reglas de inferencia](../build/inference-rules.md)