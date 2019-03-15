---
title: Definir una regla
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: cd82dc5b0693e563fd3d75a0215265089ff57913
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827184"
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

[Rutas de búsqueda en reglas](search-paths-in-rules.md)

## <a name="see-also"></a>Vea también

[Reglas de inferencia](inference-rules.md)
