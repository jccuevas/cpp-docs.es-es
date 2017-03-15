---
title: "strerror_s, _strerror_s, _wcserror_s, __wcserror_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__wcserror_s"
  - "_strerror_s"
  - "_wcserror_s"
  - "strerror_s"
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
  - "wcserror_s"
  - "__wcserror_s"
  - "_tcserror_s"
  - "_wcserror_s"
  - "tcserror_s"
  - "strerror_s"
  - "_strerror_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__wcserror_s (función)"
  - "_strerror_s (función)"
  - "_tcserror_s (función)"
  - "_wcserror_s (función)"
  - "mensajes de error, obtener"
  - "mensajes de error, imprimir"
  - "imprimir mensajes de error"
  - "strerror_s (función)"
  - "tcserror_s (función)"
  - "wcserror_s (función)"
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# strerror_s, _strerror_s, _wcserror_s, __wcserror_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene un mensaje de error del sistema \(`strerror_s`, `_wcserror_s`\), o imprime un mensaje de error proporcionado por el usuario \(`_strerror_s`, `__wcserror_s`\).  Estas versiones de [strerror, \_strerror, \_wcserror, \_\_wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t _strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   const char *strErrMsg   
);  
errno_t _wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t __wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *strErrMsg   
);  
template <size_t size>  
errno_t strerror_s(  
   char (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t _strerror_s(  
   char (&buffer)[size],  
   const char *strErrMsg   
); // C++ only  
template <size_t size>  
errno_t _wcserror_s(  
   wchar_t (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t __wcserror_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *strErrMsg   
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 Búfer que va a contener la cadena de error.  
  
 `numberOfElements`  
 Tamaño del búfer.  
  
 `errnum`  
 Número de error.  
  
 `strErrMsg`  
 Mensaje proporcionado por el usuario.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### Condiciones de error  
  
|`buffer`|`numberOfElements`|`strErrMsg`|Contenido de `buffer`|  
|--------------|------------------------|-----------------|---------------------------|  
|`NULL`|any|any|no disponible|  
|any|0|any|no modificado|  
  
## Comentarios  
 La función `strerror_s` asigna `errnum` a una cadena de mensaje de error, y devuelve la cadena de `buffer`.  `_strerror_s` no toma el número de error. Usa el valor actual de `errno` para determinar el mensaje adecuado.  Ni `strerror_s` ni `_strerror_s` imprimen realmente el mensaje. Para hacerlo, se debe llamar a una función de salida como [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md):  
  
```  
if (( _access( "datafile",2 )) == -1 )  
{  
   _strerror_s(buffer, 80);  
   fprintf( stderr, buffer );  
}  
```  
  
 Si `strErrMsg` es `NULL`, `_strerror_s` devuelve una cadena en `buffer` que contiene el mensaje de error del sistema de la última llamada a biblioteca que generó un error.  La cadena del mensaje de error termina con el carácter de línea nueva \('\\n'\).  Si `strErrMsg` no es igual a `NULL`, `_strerror_s` devuelve una cadena en `buffer` que contiene \(en orden\) el mensaje de cadena, dos puntos, un espacio, el mensaje de error del sistema de la última llamada a biblioteca que generó un error, y un carácter de línea nueva.  El mensaje de cadena puede tener, como máximo, 94 caracteres.  
  
 Estas funciones truncan el mensaje de error si su longitud supera `numberOfElements` \-1.  La cadena resultante en `buffer` siempre termina con un valor NULL.  
  
 El número de error real para `_strerror_s` se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  Se obtiene acceso a los mensajes de error del sistema a través de la variable [\_sys\_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), que es una matriz de mensajes ordenados por número de error.  `_strerror_s` obtiene acceso al mensaje de error adecuado mediante el valor de `errno` como índice de la variable `_sys_errlist`.  El valor de la variable [\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se define como el número máximo de elementos de la matriz `_sys_errlist`.  Para generar resultados precisos, llame a `_strerror_s` inmediatamente después de que una rutina de biblioteca devuelva un error.  De lo contrario, las llamadas subsiguientes a `strerror_s` o `_strerror_s` pueden sobrescribir el valor de `errno`.  
  
 `_wcserror_s` y `__wcserror_s`son versiones con caracteres anchos de `strerror_s`y `_strerror_s`, respectivamente.  
  
 Estas funciones validan sus parámetros.  Si el búfer es `NULL` o si el parámetro de tamaño es 0, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, las funciones devuelven `EINVAL` y establecen `errno` en `EINVAL`.  
  
 `_strerror_s, _wcserror_s,` y `__wcserror_s`  no forman parte de la definición ANSI, si no que son extensiones de Microsoft para dicha definición.  No se deben usar si se desea disponer de portabilidad. Para obtener compatibilidad con ANSI, use  `strerror_s`  en su lugar.  
  
 En C\+\+, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcserror_s`|`strerror_s`|`strerror_s`|`_wcserror_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strerror_s`, `_strerror_s`|\<string.h\>|  
|`_wcserror_s`, `__wcserror_s`|\<string.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo de [perror](../../c-runtime-library/reference/perror-wperror.md).  
  
## Equivalente en .NET Framework  
 [System::Exception::Message](https://msdn.microsoft.com/en-us/library/system.exception.message.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror, \_wperror](../../c-runtime-library/reference/perror-wperror.md)