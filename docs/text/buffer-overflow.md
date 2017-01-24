---
title: "Desbordamiento de b&#250;fer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "desbordamientos de búfer [C++]"
  - "búferes [C++], tamaños de caracteres"
  - "MBCS [C++], desbordamiento de búfer"
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
caps.latest.revision: 8
caps.handback.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Desbordamiento de b&#250;fer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La variación de los tamaños de caracteres puede ocasionar problemas al colocar caracteres en un búfer.  Observe el código siguiente, que copia caracteres de una cadena, `sz`, en un búfer, `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 La cuestión es: ¿Se ha copiado el último byte en el byte inicial?  La siguiente estructura no soluciona el problema, porque puede desbordar el búfer potencialmente:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 La llamada a `_mbccpy` intenta realizar lo correcto: copia el carácter completo, ya sean 1 o 2 bytes.  Pero no tiene en cuenta que el último carácter copiado puede no ajustarse al tamaño del búfer si el carácter tiene un ancho de 2 bytes.  La solución correcta es la siguiente:  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Este código prueba el posible desbordamiento del búfer en la prueba del bucle, y utiliza `_mbclen` para probar el tamaño del carácter actual al que apunta `sz`.  Mediante una llamada a la función `_mbsnbcpy`, se puede sustituir el código del bucle `while` con una sola línea de código.  Por ejemplo:  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## Vea también  
 [Sugerencias de programación para MBCS](../Topic/MBCS%20Programming%20Tips.md)