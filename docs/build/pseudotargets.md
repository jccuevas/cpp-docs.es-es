---
title: Pseudodestinos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b018cd586e48f344b93b31571ba60ae9982ad4fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="pseudotargets"></a>Pseudodestinos
Un pseudodestino es una etiqueta que se utiliza en lugar de un nombre de archivo en una línea de dependencia. Se interpreta como un archivo que no existe y, por lo que no está actualizado. NMAKE supone que la marca de tiempo de un pseudodestino es la más reciente de todos sus elementos dependientes. Si no tiene dependientes, se supone que la hora actual. Si un pseudodestino se usa como destino, siempre se ejecutan sus comandos. Un pseudodestino utilizado como un dependiente también debe aparecer como un destino en otra dependencia. Sin embargo, esa dependencia no necesita tener un bloque de comandos.  
  
 Nombres de pseudodestinos siguen las reglas de sintaxis de nombre de archivo para los destinos. Sin embargo, si el nombre no tiene una extensión (es decir, no contiene un punto), se puede superar el límite de 8 caracteres para los nombres de archivo y puede tener hasta 256 caracteres.  
  
## <a name="see-also"></a>Vea también  
 [Destinos](../build/targets.md)