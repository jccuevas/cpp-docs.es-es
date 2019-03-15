---
title: Destinos
ms.date: 11/04/2016
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
ms.openlocfilehash: 4bb80b01993ee3f3715f551c73337cf24cd43f2c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826624"
---
# <a name="targets"></a>Destinos

En una línea de dependencia, especifique uno o varios destinos, mediante cualquier nombre de archivo válido, el nombre del directorio o [pseudodestino](pseudotargets.md). Separe varios destinos con uno o más espacios o tabulaciones. Los destinos no distinguen mayúsculas de minúsculas. Se permiten rutas de acceso con los nombres de archivo. Un destino no puede superar los 256 caracteres. Si el destino que precede la coma es un único carácter, utilice un espacio de separación. en caso contrario, NMAKE interpreta la combinación de letras de dos puntos como un especificador de unidad.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Pseudodestinos](pseudotargets.md)

[Varios destinos](multiple-targets.md)

[Dependencias acumuladas](cumulative-dependencies.md)

[Destinos de bloques de descripción múltiples](targets-in-multiple-description-blocks.md)

[Efectos de dependencia](dependency-side-effects.md)

## <a name="see-also"></a>Vea también

[Bloques de descripción](description-blocks.md)