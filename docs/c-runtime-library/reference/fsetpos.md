---
title: "fsetpos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fsetpos"
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
  - "fsetpos"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fsetpos (función)"
  - "secuencias, establecer indicadores de posición"
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# fsetpos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece la marca de la secuencia\- posición.  
  
## Sintaxis  
  
```  
int fsetpos(   
   FILE *stream,  
   const fpos_t *pos   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
 `pos`  
 Almacenamiento de Posición\- indicador.  
  
## Valor devuelto  
 Si es correcto, `fsetpos` devuelve 0.  En el error, la función devuelve un valor distinto de cero y establece `errno` a una de las constantes de manifiesto siguientes \(definidas en ERRNO.H\): `EBADF`, lo que significa que el archivo no es accesible u objeto a los que los puntos de `stream` no es una estructura de archivos válida; o `EINVAL`, que significa un valor no válido para `stream` o `pos` se ha pasado.  Si se pasa un parámetro no válido en, estas funciones se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## Comentarios  
 La función de `fsetpos` establece la marca del archivo \(el archivo posición para `stream` al valor de *`pos`,* que se obtiene en una llamada anterior a `fgetpos` con *`stream`.* La función borra la marca de fin de archivo y deshace cualquier efecto de [ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md) en *`stream`.* Después de llamar a `fsetpos`, la siguiente operación en `stream` se puede entrar o salir.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fsetpos`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [fgetpos](../../c-runtime-library/reference/fgetpos.md).  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)