---
title: "_configthreadlocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_configthreadlocale"
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
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_configthreadlocale"
  - "configthreadlocale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_configthreadlocale (función)"
  - "configthreadlocale (función)"
  - "configuraciones regionales, por subproceso"
  - "configuración regional por subproceso"
  - "configuración regional de subproceso"
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _configthreadlocale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Configurar las opciones de configuración regional por subproceso.  
  
## Sintaxis  
  
```  
int _configthreadlocale(  
   int type  
);  
```  
  
#### Parámetros  
 `type`  
 Opción que se va a establecer.  Una de las opciones que se citan en la tabla siguiente.  
  
## Valor devuelto  
 Estado anterior de la configuración regional por subproceso \(`_DISABLE_PER_THREAD_LOCALE` o `_ENABLE_PER_THREAD_LOCALE`\), o \-1 si se produce un error.  
  
## Comentarios  
 La función `_configurethreadlocale` se utiliza para controlar el uso de configuraciones regionales específicas de subproceso.  Use una de estas opciones para especificar o determinar el estado de la configuración regional por subproceso:  
  
 `_ENABLE_PER_THREAD_LOCALE`  
 Hace que el subproceso actual use una configuración regional específica del subproceso.  Las llamadas subsiguientes a `setlocale` en este subproceso solo afectan a la configuración regional propia del subproceso.  
  
 `_DISABLE_PER_THREAD_LOCALE`  
 Hace que el subproceso actual use la configuración regional global.  Las llamadas subsiguientes a `setlocale` en este subproceso afectan a los demás subprocesos que usen la configuración regional global.  
  
 `0`  
 Recupera el valor actual de este subproceso concreto.  
  
 Estas funciones afectan al comportamiento de `setlocale`, `_tsetlocale`, `_wsetlocale`, `_beginthread` y  `_beginthreadex`.  Si se usa otro método para crear subprocesos, los ajustes de la configuración regional no tienen ningún efecto sobre esos subprocesos.  
  
 Cuando se deshabilita la configuración regional por subproceso, cualquier llamada subsiguiente a `setlocale` o `_wsetlocale` cambia la configuración regional de todos los subprocesos.  Cuando se habilita la configuración regional por subproceso, `setlocale` o `_wsetlocale` afecta solo a la configuración regional del subproceso actual.  
  
 Si usa `_configurethreadlocale` para habilitar una configuración regional por subproceso, se recomienda llamar a `setlocale` o `_wsetlocale` para establecer la configuración regional preferida en ese subproceso inmediatamente después.  
  
 Si `type` no es uno de los valores mencionados en la tabla, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, esta función establece `errno` en `EINVAL` y devuelve \-1.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_configthreadlocale`|\<locale.h\>|  
  
## Ejemplo  
  
```  
// crt_configthreadlocale.cpp  
//   
// This program demonstrates the use of _configthreadlocale when  
// using is two independent threads.  
//  
  
#include <locale.h>  
#include <process.h>  
#include <windows.h>  
#include <stdio.h>  
#include <time.h>  
  
#define BUFF_SIZE 100  
  
// Retrieve the date and time in the current  
// locale's format.  
int get_time(unsigned char* str)  
{  
    __time64_t  ltime;  
    struct tm   thetime;  
  
    // Retieve the time  
    _time64(&ltime);  
    _gmtime64_s(&thetime, &ltime);  
  
    // Format the current time structure into a string  
    // using %#x is the long date representation,  
    // appropriate to the current locale  
    if (!strftime((char *)str, BUFF_SIZE, "%#x",   
                  (const struct tm*)&thetime))  
    {  
        printf("strftime failed!\n");  
        return -1;  
    }  
    return 0;  
}  
  
// This thread sets its locale to German  
// and prints the time.  
unsigned __stdcall SecondThreadFunc( void* pArguments )  
{  
    unsigned char str[BUFF_SIZE];  
  
    // Set the thread code page  
    _setmbcp(_MB_CP_ANSI)  
  
    // Set the thread locale  
    printf("The thread locale is now set to %s.\n",  
           setlocale(LC_ALL, "German"));  
  
    // Retrieve the time string from the helper function  
    if (get_time(str) == 0)  
    {  
        printf("The time in German locale is: '%s'\n", str);  
    }  
  
    _endthreadex( 0 );  
    return 0;  
}   
  
// The main thread spawns a second thread (above) and then  
// sets the locale to English and prints the time.  
int main()  
{   
    HANDLE          hThread;  
    unsigned        threadID;  
    unsigned char   str[BUFF_SIZE];  
  
    // Configure per-thread locale to cause all subsequently created   
    // threads to have their own locale.  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
  
    // Retrieve the time string from the helper function  
    printf("The thread locale is now set to %s.\n",  
           setlocale(LC_ALL, "English"));  
  
    // Create the second thread.  
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,  
                                      NULL, 0, &threadID );  
  
    if (get_time(str) == 0)  
    {  
        // Retrieve the time string from the helper function  
        printf("The time in English locale is: '%s'\n\n", str);  
    }  
  
    // Wait for the created thread to finish.  
    WaitForSingleObject( hThread, INFINITE );  
  
    // Destroy the thread object.  
    CloseHandle( hThread );  
}  
```  
  
  **La configuración regional del subproceso está ahora establecida en English\_United States.1252.**  
**La fecha en la configuración regional de inglés es: 'Wednesday, May 12, 2004'**  
**La configuración regional del subproceso está ahora establecida en German\_Germany.1252.**  
**La fecha en la configuración regional es: 'Mittwoch, 12.  Mai 2004'**    
## Equivalente en .NET Framework  
 No es aplicable Con todo, vea [Usar la propiedad CurrentCulture](http://msdn.microsoft.com/es-es/3156042d-6082-4205-90b4-c917ae6a3ba6).  
  
## Vea también  
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_beginthread, \_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Subprocesamiento múltiple y configuraciones regionales](../../parallel/multithreading-and-locales.md)