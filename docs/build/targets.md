---
title: Destinos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- targets, specifying in NMAKE
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a07947dc7de4529d8cef3aa0f104d529d0b95ea5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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