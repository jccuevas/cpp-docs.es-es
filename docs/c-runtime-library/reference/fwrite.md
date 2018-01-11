---
title: fwrite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fwrite
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords: fwrite
dev_langs: C++
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b830dfd7b0a9dace46336f8f02da14fc268daf6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fwrite"></a>fwrite
Escribe datos en un flujo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t fwrite(  
   const void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buffer`  
 Puntero a los datos que se van a escribir.  
  
 `size`  
 Tamaño del elemento en bytes.  
  
 `count`  
 Número máximo de elementos que se va a escribir.  
  
 `stream`  
 Puntero a la estructura `FILE` .  
  
## <a name="return-value"></a>Valor devuelto  
 `fwrite` devuelve el número de elementos completos escritos realmente, que puede ser menor que `count` si se produce un error. De igual modo, si se produce un error, no se podrá conocer el indicador de posición de archivo. Si `stream` o `buffer` es un puntero nulo, o si un número impar de bytes que se debe escribir se especifica en modo Unicode, la función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece `errno` en `EINVAL` y devuelve 0.  
  
## <a name="remarks"></a>Comentarios  
 La función `fwrite` escribe un máximo de `count` elementos (con una longitud de `size` cada uno) desde el `buffer` al `stream` de salida. El puntero de archivo asociado a `stream` (si lo hay) se incrementa según el número de bytes escritos realmente. Si `stream` se abre en modo de texto, cada salto de línea se reemplaza por un retorno de carro y avance de línea par. Este reemplazo no tiene efecto alguno en el valor devuelto.  
  
 Cuando `stream` se abre en un modo de conversión Unicode (por ejemplo, si `stream` se abre llamando a `fopen` y usando un parámetro de modo que incluye `ccs=UNICODE`, `ccs=UTF-16LE` o `ccs=UTF-8`, o si el modo se cambia a un modo de conversión Unicode mediante `_setmode` y un parámetro de modo que incluye `_O_WTEXT`, `_O_U16TEXT` o `_O_U8TEXT`), el `buffer` se interpretará como un puntero a una matriz de `wchar_t` que contiene datos UTF-16. Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.  
  
 Como esta función bloquea el subproceso de llamada, es segura para los subprocesos. Para obtener una versión que no sea de bloqueo, vea `_fwrite_nolock`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fwrite`|\<stdio.h>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [fread](../../c-runtime-library/reference/fread.md).  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [_fwrite_nolock](../../c-runtime-library/reference/fwrite-nolock.md)   
 [_write](../../c-runtime-library/reference/write.md)