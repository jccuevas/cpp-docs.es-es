---
title: setvbuf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: setvbuf
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
f1_keywords: setvbuf
dev_langs: C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0855982627c60c51ec5753031ae932ffd430f024
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="setvbuf"></a>setvbuf
Controla el almacenamiento en búfer de la secuencia y el tamaño del búfer.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int setvbuf(  
   FILE *stream,  
   char *buffer,  
   int mode,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura `FILE` .  
  
 `buffer`  
 Búfer asignado por el usuario.  
  
 `mode`  
 Modo de almacenamiento en búfer.  
  
 `size`  
 Tamaño del búfer en bytes. Intervalo permitido: 2 <= `size` <= INT_MAX (2147483647). Internamente, el valor proporcionado para `size` se redondea hacia abajo al múltiplo más próximo a 2.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve 0.  
  
 Si `stream` es `NULL`, o si `mode` o `size` no están dentro de un cambio válido, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `setvbuf` permite que el programa controle tanto el almacenamiento en búfer como el tamaño del búfer de `stream`. `stream` debe hacer referencia a un archivo abierto que no haya sufrido ninguna operación de E/S desde que se abrió. La matriz señalada por `buffer` sirve como búfer, a menos que sea `NULL`, en cuyo caso `setvbuf` usa un búfer asignado automáticamente con una longitud de `size`/2 * 2 bytes.  
  
 El modo debe ser `_IOFBF`, `_IOLBF` o `_IONBF`. Si `mode` es `_IOFBF` o `_IOLBF`, se usa `size` como tamaño del búfer. Si `mode` es `_IONBF`, la secuencia no se almacena en búfer y `size` y `buffer` se omiten. Los valores de `mode` y sus significados son los siguientes:  
  
 `_IOFBF`  
 Almacenamiento en búfer completo; es decir, `buffer` sirve como búfer y `size` se usa como tamaño del búfer. Si `buffer` es `NULL`, se usa un búfer asignado automáticamente de `size` bytes.  
  
 `_IOLBF`  
 En algunos sistemas, esto proporciona un almacenamiento en búfer en línea, pero para Win32 el comportamiento es el mismo que `_IOFBF` (almacenamiento en búfer completo).  
  
 `_IONBF`  
 No se usa ningún búfer, independientemente de `buffer` o `size`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`setvbuf`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_setvbuf.c  
// This program opens two streams: stream1  
// and stream2. It then uses setvbuf to give stream1 a  
// user-defined buffer of 1024 bytes and stream2 no buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[1024];  
   FILE *stream1, *stream2;  
  
   if( fopen_s( &stream1, "data1", "a" ) == 0 &&  
       fopen_s( &stream2, "data2", "w" ) == 0 )  
   {  
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )  
         printf( "Incorrect type or size of buffer for stream1\n" );  
      else  
         printf( "'stream1' now has a buffer of 1024 bytes\n" );  
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )  
         printf( "Incorrect type or size of buffer for stream2\n" );  
      else  
         printf( "'stream2' now has no buffer\n" );  
      _fcloseall();  
   }  
}  
```  
  
```Output  
'stream1' now has a buffer of 1024 bytes  
'stream2' now has no buffer  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setbuf](../../c-runtime-library/reference/setbuf.md)