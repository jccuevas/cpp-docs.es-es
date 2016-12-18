---
title: "_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbcpunct_l"
  - "_ismbcblank"
  - "_ismbcprint"
  - "_ismbcgraph_l"
  - "_ismbcblank_l"
  - "_ismbcpunct"
  - "_ismbcprint_l"
  - "_ismbcspace_l"
  - "_ismbcspace"
  - "_ismbcgraph"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ismbcspace"
  - "_ismbcgraph"
  - "_ismbcpunct"
  - "ismbcspace_l"
  - "ismbcgraph"
  - "_ismbcgraph_l"
  - "_ismbcprint"
  - "_ismbcspace_l"
  - "ismbcprint"
  - "ismbcgraph_l"
  - "ismbcspace"
  - "ismbcpunct"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbcgraph (función)"
  - "_ismbcgraph_l (función)"
  - "_ismbcprint (función)"
  - "_ismbcprint_l (función)"
  - "_ismbcpunct (función)"
  - "_ismbcpunct_l (función)"
  - "_ismbcspace (función)"
  - "_ismbcspace_l (función)"
  - "ismbcgraph (función)"
  - "ismbcgraph_l (función)"
  - "ismbcprint (función)"
  - "ismbcprint_l (función)"
  - "ismbcpunct (función)"
  - "ismbcpunct_l (función)"
  - "ismbcspace (función)"
  - "ismbcspace_l (función)"
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si el carácter es un carácter gráfico, un carácter de presentación, un carácter de puntuación o un carácter de espacio.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _ismbcgraph(  
   unsigned int c   
);  
int _ismbcgraph_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcprint(  
   unsigned int c   
);  
int _ismbcprint_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcpunct(  
   unsigned int c  
);  
int _ismbcpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcblank(  
   unsigned int c   
);  
int _ismbcblank_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcspace(  
   unsigned int c   
);  
int _ismbcspace_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a determinar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple.  Si `c` \<\= 255 y hay una rutina `_ismbb` correspondiente \(por ejemplo, `_ismbcalnum` corresponde a `_ismbbalnum`\), el resultado es el valor devuelto de la rutina `_ismbb` correspondiente.  
  
 Las versiones de estas funciones son idénticas, excepto que las que tienen el sufijo `_l` usan la configuración regional que se pasa para su comportamiento dependiente de la configuración regional en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Comentarios  
 Cada una de estas funciones prueba si un carácter multibyte dado cumple una condición determinada.  
  
|Rutina|Condición de prueba|Ejemplo de la página de códigos 932|  
|------------|-------------------------|-----------------------------------------|  
|`_ismbcgraph`|Gráfico|Devuelve un valor distinto de cero si y solo si `c` es una representación de un solo byte de cualquier carácter imprimible ASCII o katakana excepto un espacio en blanco \( \).|  
|`_ismbcprint`|Carácter imprimible|Devuelve un valor distinto de cero si y solo si `c` es una representación de un solo byte de cualquier carácter imprimible ASCII o katakana, incluso un espacio en blanco \( \).|  
|`_ismbcpunct`|Puntuación|Devuelve un valor distinto de cero si y solo si `c` es una representación de un solo byte de cualquier carácter de puntuación ASCII o katakana.|  
|`_ismbcblank`|Espacio o tabulación horizontal|Devuelve un valor distinto de cero si y solo si `c` es un carácter de espacio o de tabulación horizontal: `c`\=0x20 o `c`\=0x09.|  
|`_ismbcspace`|Espacio en blanco|Devuelve un valor distinto de cero si y solo si `c` es un carácter de espacio en blanco: `c`\=0x20 o 0x09\=\<`c`\<\=0x0D.|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ismbcgraph`|\<mbstring.h\>|  
|`_ismbcgraph_l`|\<mbstring.h\>|  
|`_ismbcprint`|\<mbstring.h\>|  
|`_ismbcprint_l`|\<mbstring.h\>|  
|`_ismbcpunct`|\<mbstring.h\>|  
|`_ismbcpunct_l`|\<mbstring.h\>|  
|`_ismbcblank`|\<mbstring.h\>|  
|`_ismbcblank_l`|\<mbstring.h\>|  
|`_ismbcspace`|\<mbstring.h\>|  
|`_ismbcspace_l`|\<mbstring.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
  
-   [System::Char::IsPunctuation](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)  
  
-   [System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)  
  
-   Para `_ismbcgraph` y `_ismbcprint`: No aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_ismbc \(Rutinas\)](../../c-runtime-library/ismbc-routines.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)