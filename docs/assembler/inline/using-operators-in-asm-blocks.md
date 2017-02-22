---
title: "Usar operadores en bloques __asm | Microsoft Docs"
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
  - "__asm (palabra clave) [C++], operadores"
  - "corchetes [ ]"
  - "corchetes [ ], __asm (bloques)"
  - "operadores [C++], usar en bloques __asm"
  - "corchetes [ ]"
  - "corchetes [ ], __asm (bloques)"
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Usar operadores en bloques __asm
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Un bloque `__asm` no puede usar los operadores específicos de C o C\+\+, como el operador **\<\<**.  Sin embargo, operadores compartidos por C y MASM, como el operador \*, se interpretan como operadores del lenguaje de ensamblado.  Por ejemplo, fuera de un bloque `__asm`, los corchetes \(**\[ \]**\) se interpretan como subíndices de matriz de inclusión, que C ajusta automáticamente al tamaño de un elemento de la matriz.  Dentro de un bloque `__asm`, se ven como el operador índice de MASM, que produce un desplazamiento de bytes sin ajuste de escala desde cualquier objeto de datos o etiqueta \(no solo una matriz\).  El código siguiente ilustra la diferencia:  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 La primera referencia a `array` no se ajusta a escala, pero la segunda sí.  Observe que puede utilizar el operador **TYPE** para lograr el ajuste de escala basándose en una constante.  Por ejemplo, las instrucciones siguientes son equivalentes:  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar C o C\+\+ en bloques \_\_asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)