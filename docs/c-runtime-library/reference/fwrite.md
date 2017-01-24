---
title: "fwrite | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fwrite"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fwrite"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fwrite (función)"
  - "secuencias, escribir datos en"
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fwrite
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe datos en un flujo.  
  
## Sintaxis  
  
```  
size_t fwrite(    const void *buffer,    size_t size,    size_t count,    FILE *stream  );  
```  
  
#### Parámetros  
 `buffer`  
 Puntero a los datos que se van a escribir.  
  
 `size`  
 Tamaño del elemento en bytes.  
  
 `count`  
 Número máximo de elementos que se va a escribir.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 `fwrite` devuelve el número de elementos completos escritos realmente, que puede ser menor que `count` si se produce un error.  De igual modo, si se produce un error, no se podrá conocer el indicador de posición de archivo.  Si `stream` o `buffer` es un puntero nulo, o si un número impar de bytes que se debe escribir se especifica en modo Unicode, esta función invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, esta función establece `errno` en `EINVAL` y devuelve 0.  
  
## Comentarios  
 La función `fwrite` escribe un máximo de `count` elementos \(con una longitud de `size` cada uno\) desde el `buffer` al `stream` de salida.  El puntero de archivo asociado a `stream` \(si lo hay\) se incrementa según el número de bytes escritos realmente.  Si el `stream` se abre en modo de texto, cada salto de línea se reemplazará por un par de retorno de carro\-avance de línea.  Este reemplazo no tiene efecto alguno en el valor devuelto.  
  
 Cuando `stream` se abre en un modo de conversión Unicode \(por ejemplo, si `stream` se abre llamando a `fopen` y usando un parámetro de modo que incluye `ccs=UNICODE`, `ccs=UTF-16LE` o `ccs=UTF-8`, o si el modo se cambia a un modo de conversión Unicode mediante `_setmode` y un parámetro de modo que incluye `_O_WTEXT`, `_O_U16TEXT` o `_O_U8TEXT`\), el `buffer` se interpretará como un puntero a una matriz de `wchar_t` que contiene datos UTF\-16.  Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.  
  
 Como esta función bloquea el subproceso de llamada, es segura para los subprocesos.  Para consultar una versión que no realiza el bloqueo, vea `_fwrite_nolock`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fwrite`|\<stdio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Consulte el ejemplo de [fread](../../c-runtime-library/reference/fread.md).  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Write](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_fwrite\_nolock](../../c-runtime-library/reference/fwrite-nolock.md)   
 [\_write](../../c-runtime-library/reference/write.md)