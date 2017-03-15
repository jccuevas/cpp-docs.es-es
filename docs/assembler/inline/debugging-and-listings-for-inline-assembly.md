---
title: "Depuraci&#243;n y listas para el ensamblado alineado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm (palabra clave) [C++], depurar"
  - "errores, __asm (bloques)"
  - "depurar [C++], código de ensamblado en línea"
  - "ensamblado en línea, depurar"
  - "ensamblado en línea, listas"
  - "depurador de nivel de origen"
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Depuraci&#243;n y listas para el ensamblado alineado
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Los programas que contienen código de ensamblado insertado se pueden depurar con un depurador de nivel de origen si los compila con la opción [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 En el depurador, puede establecer puntos de interrupción en las líneas de C o C\+\+ y de lenguaje de ensamblado.  Si habilita el modo de ensamblado mixto y de origen, puede mostrar la forma de origen y desensamblada del código de ensamblado.  
  
 Tenga en cuenta que la inclusión de varias instrucciones de ensamblado o del lenguaje de origen en una línea pueden dificultar la depuración.  En modo de origen, puede utilizar el depurador para establecer puntos de interrupción en una línea, pero no en instrucciones individuales en la misma línea.  El mismo principio se aplica a un bloque `__asm` definido como una macro de C, que se expande en una sola línea lógica.  
  
 Si crea un listado mixto de lenguaje de origen y de ensamblado con la opción del compilador [\/FAs](../../build/reference/fa-fa-listing-file.md), el listado contiene las formas de origen y de ensamblado de cada línea del lenguaje de ensamblado.  Las macros no se expanden en listados, sino durante la compilación.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar lenguaje de ensamblado en bloques \_\_asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)