---
title: Destinos | Documentos de Microsoft
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
ms.openlocfilehash: 79e9d72d2b2fb999d987a6781caace9a0360facb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380267"
---
# <a name="targets"></a>Destinos
En una línea de dependencia, se pueden especificar uno o varios destinos usando cualquier nombre de archivo válido, el nombre del directorio o [pseudodestino](../build/pseudotargets.md). Separe varios destinos con uno o más espacios o tabulaciones. Destinos no distinguen mayúsculas de minúsculas. Se permiten rutas de acceso con nombres de archivo. Un destino no puede superar los 256 caracteres. Si el destino que precede el carácter de dos puntos es un único carácter, utilice un espacio de separación; de lo contrario, NMAKE interpreta la combinación de letras de dos puntos como un especificador de unidad.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
 [Pseudodestinos](../build/pseudotargets.md)  
  
 [Varios destinos](../build/multiple-targets.md)  
  
 [Dependencias acumuladas](../build/cumulative-dependencies.md)  
  
 [Destinos de bloques de descripción múltiples](../build/targets-in-multiple-description-blocks.md)  
  
 [Efectos secundarios de dependencia](../build/dependency-side-effects.md)  
  
## <a name="see-also"></a>Vea también  
 [Bloques de descripción](../build/description-blocks.md)