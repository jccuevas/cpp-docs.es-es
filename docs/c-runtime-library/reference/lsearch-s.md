---
title: "_lsearch_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lsearch_s"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_lsearch_s"
  - "lsearch_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lsearch_s (función)"
  - "matrices [CRT], buscar"
  - "claves, buscar en matrices"
  - "búsqueda lineal"
  - "lsearch_s (función)"
  - "buscar, lineales"
  - "valores, buscar"
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lsearch_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza una búsqueda lineal por un valor.  Una versión de [\_lsearch](../../c-runtime-library/reference/lsearch.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
void *_lsearch_s(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### Parámetros  
 `key`  
 Objeto para buscar.  
  
 `base`  
 Puntero a la base de la matriz que se buscará.  
  
 `num`  
 Número de elementos.  
  
 `size`  
 Tamaño de cada elemento de matriz de bytes.  
  
 `compare`  
 Puntero a la rutina de comparación.  El segundo parámetro es un puntero a la clave de búsqueda.  El tercer parámetro es un puntero a un elemento de matriz que se va a comparar con la clave.  
  
 `context`  
 Un puntero a un objeto que se puede tener acceso en la función de comparación.  
  
## Valor devuelto  
 Si se encuentra `key` , `_lsearch_s` devuelve un puntero al elemento de matriz en `base` que coincide con `key`.  Si `key` no se encuentra, `_lsearch_s` devuelve un puntero al elemento recién agregado al final de la matriz.  
  
 Si los parámetros no válidos se pasan a la función, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, después `errno` se establece en `EINVAL` y la función devuelve `NULL`.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### Condiciones de error  
  
|`key`|`base`|`compare`|`num`|`size`|`errno`|  
|-----------|------------|---------------|-----------|------------|-------------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|cero|`EINVAL`|  
|any|any|`NULL`|an|any|`EINVAL`|  
  
## Comentarios  
 La función de `_lsearch_s` realiza una búsqueda lineal por valor `key` en una matriz de elementos de `num` , cada uno de los bytes de `width` .  A diferencia de `bsearch_s`, `_lsearch_s` no requiere una matriz ajustar su tamaño.  Si `key` no se encuentra, después `_lsearch_s` lo agrega al final de la matriz y aumenta `num`.  
  
 La función de `compare` es un puntero a una rutina usuario\- proporcionada que compara dos elementos de matriz y devuelve un valor que especifica la relación.  La función de `compare` también contiene el puntero el contexto como primer argumento.  `_lsearch_s` llama `compare` una o más veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada.  `compare` debe comparar los elementos y después devolver cero \(indican los elementos sea diferente\) o 0 \(indican los elementos sea idéntico\).  
  
 El puntero de `context` puede ser útil si la estructura de datos que se busca es parte de un objeto y la función de `compare` necesita tener acceso a los miembros del objeto.  Por ejemplo, el código de la función de `compare` puede convertir el puntero vacío en el tipo de objeto adecuado y tener acceso a los miembros de ese objeto.  La adición del puntero de `context` crea `_lsearch_s` más seguro porque el contexto adicional se puede utilizar para evitar los errores de reentrada asociados al uso de variables estáticas que los datos estén disponibles para la función de `compare` .  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_lsearch_s`|\<search.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)