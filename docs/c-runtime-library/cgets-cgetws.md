---
title: "_cgets, _cgetws | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cgetws"
  - "_cgets"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "cgetws"
  - "_cgetws"
  - "_cgets"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cgets (función)"
  - "_cgetws (función)"
  - "cgets (función)"
  - "cgetws (función)"
  - "consola, obtener cadenas de"
  - "cadenas [C++], obtener de consola"
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
caps.latest.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 32
---
# _cgets, _cgetws
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene una cadena de caracteres de la consola. Hay disponibles versiones más seguras de estas funciones; vea [\_cgets\_s, \_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT. Las versiones seguras de estas funciones, \_cgets\_s y \_cgetws\_s, siguen estando disponibles. Para obtener información sobre estas funciones alternativas, vea [\_cgets\_s, \_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_cgets(   
   char *buffer   
);  
wchar_t *_cgetws(  
   wchar_t *buffer  
);  
template <size_t size>  
char *_cgets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_cgetws(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento de los datos.  
  
## Valor devuelto  
 `_cgets` y `_cgetws` devuelven un puntero al principio de la cadena, en `buffer[2]`. Si `buffer` es `NULL`, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelven `NULL` y establecen `errno` en `EINVAL`.  
  
## Comentarios  
 Estas funciones leen una cadena de caracteres de la consola y almacenan la cadena y su longitud en la ubicación que indica `buffer`. El parámetro `buffer` debe ser un puntero a una matriz de caracteres. El primer elemento de la matriz, `buffer[0]`, debe contener la longitud máxima \(en caracteres\) de la cadena que se va a leer. La matriz debe tener suficientes elementos para contener la cadena, un carácter de terminación nulo \('\\0'\) y 2 bytes adicionales. La función lee los caracteres hasta una combinación de retorno de carro–salto de línea \(CR\-LF\), o hasta que se lee el número de caracteres especificado. La cadena se almacena a partir de `buffer[2]`. Si la función lee una combinación CR\-LF, almacena el carácter nulo \('\\0'\). A continuación, la función almacena la longitud real de la cadena en el segundo elemento de la matriz, `buffer[1]`.  
  
 Como todas las claves de edición están activas cuando se llama a `_cgets` o`_cgetws` desde una ventana de la consola, al presionar F3 se repite la última entrada.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_cgets`|\<conio.h\>|  
|`_cgetws`|\<conio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_cgets.c // compile with: /c /W3 // This program creates a buffer and initializes // the first byte to the size of the buffer. Next, the // program accepts an input string using _cgets and displays // the size and text of that string. #include <conio.h> #include <stdio.h> #include <errno.h> int main( void ) { char buffer[83] = { 80 };  // Maximum characters in 1st byte char *result; printf( "Input line of text, followed by carriage return:\n"); // Input a line of text: result = _cgets( buffer ); // C4996 // Note: _cgets is deprecated; consider using _cgets_s if (!result) { printf( "An error occurred reading from the console:" " error code %d\n", errno); } else { printf( "\nLine length = %d\nText = %s\n", buffer[1], result ); } }  
```  
  
```Output  
  
A line of input.Input line of text, followed by carriage return: Line Length = 16 Text = A line of input.  
```  
  
## Vea también  
 [E\/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)   
 [\_getch, \_getwch](../c-runtime-library/reference/getch-getwch.md)