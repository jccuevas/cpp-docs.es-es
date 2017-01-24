---
title: "strerror, _strerror, _wcserror, __wcserror | Microsoft Docs"
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
  - "strerror"
  - "_strerror"
  - "_wcserror"
  - "__wcserror"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__sys_errlist"
  - "wcserror"
  - "_strerror"
  - "__wcserror"
  - "strerror"
  - "__sys_nerr"
  - "_tcserror"
  - "_wcserror"
  - "tcserror"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__sys_errlist"
  - "__sys_nerr"
  - "__wcserror (función)"
  - "_strerror (función)"
  - "_tcserror (función)"
  - "_wcserror (función)"
  - "mensajes de error, obtener"
  - "mensajes de error, imprimir"
  - "imprimir mensajes de error"
  - "strerror (función)"
  - "tcserror (función)"
  - "wcserror (función)"
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strerror, _strerror, _wcserror, __wcserror
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene una cadena de mensaje de error del sistema \(`strerror`, `_wcserror`\) o da formato a una cadena de mensaje de error proporcionada por el usuario \(`_strerror`, `__wcserror`\).  Hay disponibles versiones más seguras de estas funciones; vea [strerror\_s, \_strerror\_s, \_wcserror\_s, \_\_wcserror\_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md).  
  
## Sintaxis  
  
```  
char *strerror(    int errnum  ); char *_strerror(    const char *strErrMsg  ); wchar_t * _wcserror(    int errnum  ); wchar_t * __wcserror(    const wchar_t *strErrMsg  );  
```  
  
#### Parámetros  
 `errnum`  
 Número de error.  
  
 `strErrMsg`  
 Mensaje proporcionado por el usuario.  
  
## Valor devuelto  
 Todas estas funciones devuelven un puntero a la cadena de mensaje de error.  Las siguientes llamadas pueden sobrescribir la cadena.  
  
## Comentarios  
 La función `strerror` asigna `errnum` a una cadena de mensaje de error y devuelve un puntero a la cadena.  Ni `strerror` ni `_strerror` imprimen el mensaje en realidad: para eso, hay que llamar a una función de salida como [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md):  
  
```  
if (( _access( "datafile",2 )) == -1 )  
   fprintf( stderr, _strerror(NULL) );  
```  
  
 Si `strErrMsg` se pasa como `NULL`, `_strerror` devuelve un puntero a una cadena que contiene el mensaje de error del sistema de la última llamada a biblioteca que generó un error.  La cadena del mensaje de error termina con el carácter de línea nueva \('\\n'\).  Si `strErrMsg` no es igual a `NULL`, `_strerror` devuelve un puntero a una cadena que contiene \(en orden\) el mensaje de cadena, dos puntos, un espacio, el mensaje de error del sistema de la última llamada a biblioteca que generó un error y, por último, un carácter de línea nueva.  El mensaje de cadena puede tener, como máximo, 94 caracteres.  
  
 El número de error real para `_strerror` se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Para generar resultados precisos, llame a `_strerror` inmediatamente después de que una rutina de biblioteca devuelva un error.  De lo contrario, las llamadas subsiguientes a `strerror` o `_strerror` pueden sobrescribir el valor de `errno`.  
  
 `_wcserror` y `__wcserror` son versiones con caracteres anchos de `strerror` y `_strerror`, respectivamente.  
  
 `_strerror`, `_wcserror` y `__wcserror` no forman parte de la definición de ANSI, sino que son extensiones de Microsoft que le aconsejamos no use si lo que quiere es código portable.  Para la compatibilidad con ANSI, use `strerror` en su lugar.  
  
 Para obtener cadenas de error, recomendamos `strerror` o `_wcserror` en lugar de las macros desusadas [\_sys\_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y [\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) y las funciones internas desusadas `__sys_errlist` y `__sys_nerr`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcserror`|`strerror`|`strerror`|`_wcserror`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strerror`|\<string.h\>|  
|`_strerror`|\<string.h\>|  
|`_wcserror`, `__wcserror`|\<string.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [perror](../../c-runtime-library/reference/perror-wperror.md).  
  
## Equivalente en .NET Framework  
 [System::Exception::Message](https://msdn.microsoft.com/en-us/library/system.exception.message.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror, \_wperror](../../c-runtime-library/reference/perror-wperror.md)