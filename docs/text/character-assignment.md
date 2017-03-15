---
title: "Asignaci&#243;n de caracteres | Microsoft Docs"
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
  - "caracteres [C++], asignaciones"
  - "MBCS [C++], asignación de caracteres"
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Asignaci&#243;n de caracteres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Observe el ejemplo siguiente, en el que el bucle `while` examina una cadena y copia todos los caracteres excepto 'X' en otra cadena:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 El código copia el byte de `sz2` en la ubicación a la que apunta `sz1`, y aumenta `sz1` para que reciba el siguiente byte.  Pero si el carácter siguiente de `sz2` es un carácter de doble byte, la asignación a `sz1` sólo copia el primer byte.  El código siguiente utiliza una función portable para copiar el carácter de forma segura y otra función para aumentar correctamente `sz1` y `sz2`:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
    {  
        _mbscpy_s( sz1, 1, sz2 );  
        sz1 = _mbsinc( sz1 );  
        sz2 = _mbsinc( sz2 );  
    }  
    else  
        sz2 = _mbsinc( sz2 );  
}  
```  
  
## Vea también  
 [Sugerencias de programación para MBCS](../Topic/MBCS%20Programming%20Tips.md)   
 [Comparación de caracteres](../text/character-comparison.md)