---
title: Destinos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: edb75258c548526c68ed33f7f8037656750f6855
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713811"
---
# <a name="targets"></a>Destinos

En una línea de dependencia, especifique uno o varios destinos, mediante cualquier nombre de archivo válido, el nombre del directorio o [pseudodestino](../build/pseudotargets.md). Separe varios destinos con uno o más espacios o tabulaciones. Los destinos no distinguen mayúsculas de minúsculas. Se permiten rutas de acceso con los nombres de archivo. Un destino no puede superar los 256 caracteres. Si el destino que precede la coma es un único carácter, utilice un espacio de separación. en caso contrario, NMAKE interpreta la combinación de letras de dos puntos como un especificador de unidad.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Pseudodestinos](../build/pseudotargets.md)

[Varios destinos](../build/multiple-targets.md)

[Dependencias acumuladas](../build/cumulative-dependencies.md)

[Destinos de bloques de descripción múltiples](../build/targets-in-multiple-description-blocks.md)

[Efectos de dependencia](../build/dependency-side-effects.md)

## <a name="see-also"></a>Vea también

[Bloques de descripción](../build/description-blocks.md)