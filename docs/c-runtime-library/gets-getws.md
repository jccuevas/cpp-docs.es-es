---
title: "gets, _getws | Microsoft Docs"
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
  - "_getws"
  - "gets"
apilocation: 
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getts"
  - "gets"
  - "_getws"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getts (función)"
  - "_getws (función)"
  - "gets (función)"
  - "getts (función)"
  - "getws (función)"
  - "líneas, obtener"
  - "entrada estándar, leer"
  - "secuencias, obtener líneas"
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
caps.latest.revision: 32
caps.handback.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# gets, _getws
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene una línea del flujo `stdin`. Hay disponibles versiones más seguras de estas funciones; vea [gets\_s, \_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md).  
  
> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT. Las versiones seguras de estas funciones, gets\_s y \_getws\_s, siguen estando disponibles. Para obtener información sobre estas funciones alternativas, vea [gets\_s, \_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *gets(   
   char *buffer   
);  
wchar_t *_getws(   
   wchar_t *buffer   
);  
template <size_t size>  
char *gets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento de la cadena de entrada.  
  
## Valor devuelto  
 Devuelve su argumento si se realiza correctamente. Un puntero `NULL` indica un error o una condición de fin de archivo. Utilice [ferror](../c-runtime-library/reference/ferror.md) o [feof](../c-runtime-library/reference/feof.md) para determinar qué resultado se ha producido. Si `buffer` es `NULL`, estas funciones invocan un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven `NULL` y establecen errno en `EINVAL`.  
  
## Comentarios  
 La función `gets` lee una línea del flujo de entrada estándar `stdin` y la almacena en `buffer`. La línea consta de todos los caracteres hasta el primer carácter de línea nueva \('\\n'\), este último incluido. A continuación, `gets` reemplaza el carácter de línea nueva con un carácter nulo \('\\0'\) antes de devolver la línea. Por su parte, la función `fgets` conserva el carácter de línea nueva.`_getws` es una versión con caracteres anchos de `gets`; el argumento y el valor devuelto son cadenas de caracteres anchos.  
  
> [!IMPORTANT]
>  No hay forma de limitar el número de caracteres que gets lee, por lo que una entrada que no sea de confianza puede producir fácilmente saturaciones del búfer. Utilice `fgets` en su lugar.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_getts`|`gets`|`gets`|`_getws`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`gets`|\<stdio.h\>|  
|`_getws`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_gets.c // compile with: /WX /W3 #include <stdio.h> int main( void ) { char line[21]; // room for 20 chars + '\0' gets( line );  // C4996 // Danger: No way to limit input to 20 chars. // Consider using gets_s instead. printf( "The line entered was: %s\n", line ); }  
```  
  
 Observe que una entrada de más 20 caracteres saturará el búfer de líneas y provocará casi con seguridad que el programa se bloquee.  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## Equivalente en .NET Framework  
 [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## Vea también  
 [E\/S de secuencia](../c-runtime-library/stream-i-o.md)   
 [fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)   
 [puts, \_putws](../c-runtime-library/reference/puts-putws.md)