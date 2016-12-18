---
title: "mbrlen | Microsoft Docs"
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
  - "mbrlen"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbrlen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "mbrlen (función)"
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbrlen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determine el número de bytes que se necesitan para completar un carácter multibyte en la configuración regional actual, con capacidad de reinicio en medio de un carácter multibyte.  
  
## Sintaxis  
  
```  
size_t mbrlen(  
   const char * str,  
   size_t count,  
   mbstate_t * mbstate  
);  
```  
  
#### Parámetros  
 `str`  
 Puntero al siguiente byte que se va a inspeccionar en una cadena de caracteres multibyte.  
  
 `count`  
 El número máximo de bytes a inspeccionar.  
  
 `mbstate`  
 Puntero al estado de desplazamiento actual del byte inicial de `str`.  
  
## Valor devuelto  
 Uno de los siguientes valores: , , , , .  
  
 0  
 Los siguientes `count` o menos bytes completan el carácter multibyte que representa el carácter nulo ancho.  
  
 1 a `count`, ambos inclusive  
 Los próximos `count` o menos bytes completan un carácter multibyte válido.  El valor devuelto es el número de bytes que completan el carácter multibyte.  
  
 \(size\_t\)\(\-2\)  
 Los próximos `count` bytes contribuyen a un carácter multibyte incompleto pero potencialmente válido y los `count` bytes se han procesado.  
  
 \(size\_t\)\(\-1\)  
 Se produjo un error de codificación.  Los siguientes `count` o menos bytes no contribuyen a un carácter multibyte completo y válido.  En este caso, `errno` se establece a EILSEQ y el estado de la conversión en `mbstate` no está especificado.  
  
## Comentarios  
 La función `mbrlen` inspecciona a lo sumo `count` bytes a partir del byte señalado por `str` para determinar el número de bytes que son necesarios para completar el siguiente carácter multibyte, incluidas las secuencias de desplazamiento.  Es equivalente a la llamada `mbrtowc(NULL, str, count, &mbstate)`, donde `mbstate` es cualquier objeto `mbstate_t` proporcionado por el usuario, o un objeto interno estático proporcionadas por la biblioteca.  
  
 La función `mbrlen` guarda y usa el estado de desplazamiento de un carácter multibyte incompleto en el parámetro `mbstate`.  Esto da a `mbrlen` la capacidad de reiniciar en medio de un carácter multibyte si es necesario, examinando a lo sumo `count` bytes.  Si `mbstate` es un puntero nulo, `mbrlen` usa un objeto `mbstate_t` estático interno para almacenar el estado de desplazamiento.  Dado que el objeto `mbstate_t` interno no es seguro para subprocesos, se recomienda asignar y pasar siempre su propio valor para `mbstate`.  
  
 La función `mbrlen` difiere de [\_mbclen, mblen, \_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md) en que se puede reiniciar.  El estado de desplazamiento se almacena en `mbstate` para las llamadas posteriores a la misma o a otras funciones reiniciables.  Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación debe utilizar `wcsrlen` en lugar de `wcslen` si se utiliza una llamada subsiguiente a `wcsrtombs` en lugar de a `wcstombs.`  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|No aplicable|No aplicable|`mbrlen`|No aplicable|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`mbrlen`|\<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Este ejemplo muestra cómo la interpretación de caracteres multibyte depende de la página de códigos actual, y demuestra la capacidad de reanudación de `mbrlen`.  
  
```  
 // crt_mbrlen.c  
// Compile by using: cl crt_mbrlen.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <locale.h>  
#include <wchar.h>  
  
size_t Example(const char * pStr)  
{  
    size_t      charLen = 0;  
    size_t      charCount = 0;  
    mbstate_t   mbState = {0};  
  
    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&  
            charLen != (size_t)-1)  
    {  
        if (charLen != (size_t)-2) // if complete mbcs char,  
        {  
            charCount++;  
        }  
    }   
    return (charCount);  
}   
  
int main( void )  
{  
    int         cp;  
    size_t      charCount = 0;  
    const char  *pSample =   
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";  
  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
  
    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale  
    _setmbcp(932); // and Japanese multibyte code page  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
}  
```  
  
  **Code page: 0**  
**é╨éτé¬é╚: Shift\-jis hiragana.  Character count: 29**  
**Code page: 932**  
**????: Shift\-jis hiragana.  Character count: 25**    
## Equivalente en .NET Framework  
 [System::String::Length](https://msdn.microsoft.com/en-us/library/system.string.length.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)