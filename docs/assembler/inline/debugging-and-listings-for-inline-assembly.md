---
title: "Depuración y listas para el código ensamblador | Documentos de Microsoft"
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
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fea943c30d48ac122ae5d848306e4fe251f58da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Depuración y listas para el ensamblado insertado
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Se pueden depurar programas que contienen código ensamblador en línea con un depurador de nivel de origen si se compila con la [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción.  
  
 En el depurador, puede establecer puntos de interrupción en las líneas de C o C++ y de lenguaje de ensamblado. Si habilita el modo de ensamblado mixto y de origen, puede mostrar la forma de origen y desensamblada del código de ensamblado.  
  
 Tenga en cuenta que la inclusión de varias instrucciones de ensamblado o del lenguaje de origen en una línea pueden dificultar la depuración. En modo de origen, puede utilizar el depurador para establecer puntos de interrupción en una línea, pero no en instrucciones individuales en la misma línea. El mismo principio se aplica a un bloque `__asm` definido como una macro de C, que se expande en una sola línea lógica.  
  
 Si creas un origen mixto y un ensamblado con el [/FAs](../../build/reference/fa-fa-listing-file.md) opción del compilador, la lista contiene el origen y el ensamblado de formularios de cada línea de lenguaje de ensamblado. Las macros no se expanden en listados, sino durante la compilación.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)