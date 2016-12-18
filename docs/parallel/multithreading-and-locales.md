---
title: "Subprocesamiento m&#250;ltiple y configuraciones regionales | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "configuraciones regionales [C++], multithreading"
  - "subprocesamiento múltiple [C++], configuraciones regionales"
  - "configuración regional por subproceso"
  - "subprocesamiento [C++], configuraciones regionales"
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Subprocesamiento m&#250;ltiple y configuraciones regionales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La Biblioteca en tiempo de ejecución de C y el Biblioteca estándar de C\+\+ proporcionan compatibilidad para cambiar la configuración regional del programa.  Este tema aborda problemas que surgen al utilizar la funcionalidad de la configuración regional de ambas bibliotecas en una aplicación multiproceso.  
  
## Comentarios  
 Con la Biblioteca en tiempo de ejecución de C puede crear aplicaciones multiproceso mediante las funciones `_beginthread` y `_beginthreadex`.  Este tema sólo cubre las aplicaciones multiproceso creadas mediante estas funciones.  Para obtener más información, vea [\_beginthread, \_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
 Para cambiar la configuración regional mediante la Biblioteca en tiempo de ejecución de C, utilice la función [setlocale](../preprocessor/setlocale.md).  En versiones anteriores de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)], esta función siempre modificaba la configuración regional en toda la aplicación.  Ahora existe compatibilidad para establecer la configuración regional de cada subproceso.  Esto se realiza mediante la función [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md).  Para especificar que [setlocale](../preprocessor/setlocale.md) sólo debería cambiar la configuración regional en el subproceso actual, llame a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` en ese subproceso.  Al contrario, si se llama a `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` el subproceso usará la configuración regional global, y cualquier llamada a [setlocale](../preprocessor/setlocale.md) en dicho subproceso cambiará la configuración regional de todos los subprocesos que no tengan habilitada explícitamente la configuración regional para cada subproceso.  
  
 Para cambiar la configuración regional mediante la Biblioteca en tiempo de ejecución de C\+\+, utilice la función [locale \(Clase\)](../standard-library/locale-class.md).  Si se llama al método [locale::global](../Topic/locale::global.md), cambiará la configuración regional de cada subproceso que no haya habilitado explícitamente la configuración regional para cada subproceso.  Para cambiar la configuración regional de un único subproceso o parte de una aplicación, simplemente cree una instancia de un objeto `locale` en dicho subproceso o parte de código.  
  
> [!NOTE]
>  Llamar a [locale::global](../Topic/locale::global.md), cambia la configuración regional de la Biblioteca estándar de C\+\+ y la Biblioteca en tiempo de ejecución de C.  Sin embargo, llamar a [setlocale](../preprocessor/setlocale.md), sólo cambia la configuración regional de la Biblioteca en tiempo de ejecución de C; no afecta a la Biblioteca estándar de C\+\+.  
  
 Los siguientes ejemplos muestran cómo usar las funciones [setlocale](../preprocessor/setlocale.md), [locale \(Clase\)](../standard-library/locale-class.md) y [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) para cambiar la configuración regional de una aplicación en varios escenarios diferentes.  
  
## Ejemplo  
 En este ejemplo, el subproceso principal genera dos subprocesos secundarios.  El primer subproceso, el subproceso A, habilita la configuración regional para cada subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`.  El segundo subproceso, el subproceso B, así como el subproceso principal, no habilitan la configuración regional para cada subproceso.  A continuación, el subproceso A procede a cambiar la configuración regional mediante la función [setlocale](../preprocessor/setlocale.md) de la Biblioteca en tiempo de ejecución de C.  
  
 Como el subproceso A tiene habilitada la configuración regional para cada subproceso, sólo las funciones de la Biblioteca en tiempo de ejecución de C del subproceso A empezarán a utilizar la configuración regional "francesa".  Las funciones de la Biblioteca en tiempo de ejecución de C del subproceso B y del subproceso principal continuarán utilizando la configuración regional de "C."  A su vez, como [setlocale](../preprocessor/setlocale.md) no afecta a la configuración regional de la Biblioteca estándar de C\+\+, todos los objetos de ésta seguirán utilizando la configuración regional de "C".  
  
```  
// multithread_locale_1.cpp  
// compile with: /EHsc /MD  
#include <clocale>  
#include <cstdio>  
#include <locale>  
#include <process.h>  
#include <windows.h>  
  
#define NUM_THREADS 2  
using namespace std;  
  
unsigned __stdcall RunThreadA(void *params);  
unsigned __stdcall RunThreadB(void *params);  
  
BOOL localeSet = FALSE;  
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);  
  
int main()  
{  
    HANDLE threads[NUM_THREADS];  
  
    unsigned aID;  
    threads[0] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadA, NULL, 0, &aID);  
  
    unsigned bID;  
    threads[1] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadB, NULL, 0, &bID);  
  
    WaitForMultipleObjects(2, threads, TRUE, INFINITE);  
  
    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread main] locale::global is set to \"%s\"\n",  
        locale().name().c_str());  
  
    CloseHandle(threads[0]);  
    CloseHandle(threads[1]);  
    CloseHandle(printMutex);  
  
    return 0;  
}  
  
unsigned __stdcall RunThreadA(void *params)  
{  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
    setlocale(LC_ALL, "french");  
    localeSet = TRUE;  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread A] Per-thread locale is enabled.\n");  
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
  
unsigned __stdcall RunThreadB(void *params)  
{  
    while (!localeSet)  
        Sleep(100);  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
```  
  
  **\[Thread A\] Per\-thread locale is enabled.**  
**\[Subproceso A\] La configuración regional de CRT se establece en"Francés\_Francia.1252"**  
**\[Subproceso A\] locale::global se establece en "C"**  
**\[Thread B\] Per\-thread locale is NOT enabled.**  
**\[Subproceso B\] La configuración regional de CRT se establece en "C"**  
**\[Subproceso B\] configuración regional::global se establece en "C"**  
**\[Thread main\] Per\-thread locale is NOT enabled.**  
**\[Subproceso principal\] La configuración regional de CRT se establece en "C"**  
**\[Subproceso principal\] locale::global se establece en "C"**   
## Ejemplo  
 En este ejemplo, el subproceso principal genera dos subprocesos secundarios.  El primer subproceso, el subproceso A, habilita la configuración regional para cada subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`.  El segundo subproceso, el subproceso B, así como el subproceso principal, no habilitan la configuración regional para cada subproceso.  A continuación, el subproceso A procede a cambiar la configuración regional mediante el método [locale::global](../Topic/locale::global.md) de la Biblioteca estándar de C\+\+.  
  
 Como el subproceso A tiene habilitada la configuración regional para cada subproceso, sólo las funciones de la Biblioteca en tiempo de ejecución de C del subproceso A empezarán a utilizar la configuración regional "francesa".  Las funciones de la Biblioteca en tiempo de ejecución de C del subproceso B y del subproceso principal continuarán utilizando la configuración regional de "C."  Sin embargo, debido a que el método [locale::global](../Topic/locale::global.md) cambia "globalmente" la configuración regional, todos los objetos de la Biblioteca estándar de C\+\+ en todos los subprocesos empezarán a utilizar la configuración regional "francesa".  
  
```  
// multithread_locale_2.cpp  
// compile with: /EHsc /MD  
#include <clocale>  
#include <cstdio>  
#include <locale>  
#include <process.h>  
#include <windows.h>  
  
#define NUM_THREADS 2  
using namespace std;  
  
unsigned __stdcall RunThreadA(void *params);  
unsigned __stdcall RunThreadB(void *params);  
  
BOOL localeSet = FALSE;  
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);  
  
int main()  
{  
    HANDLE threads[NUM_THREADS];  
  
    unsigned aID;  
    threads[0] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadA, NULL, 0, &aID);  
  
    unsigned bID;  
    threads[1] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadB, NULL, 0, &bID);  
  
    WaitForMultipleObjects(2, threads, TRUE, INFINITE);  
  
    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread main] locale::global is set to \"%s\"\n",  
        locale().name().c_str());  
  
    CloseHandle(threads[0]);  
    CloseHandle(threads[1]);  
    CloseHandle(printMutex);  
  
    return 0;  
}  
  
unsigned __stdcall RunThreadA(void *params)  
{  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
    locale::global(locale("french"));  
    localeSet = TRUE;  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread A] Per-thread locale is enabled.\n");  
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
  
unsigned __stdcall RunThreadB(void *params)  
{  
    while (!localeSet)  
        Sleep(100);  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
```  
  
  **\[Thread A\] Per\-thread locale is enabled.**  
**\[Subproceso A\] La configuración regional de CRT se establece en"Francés\_Francia.1252"**  
**\[Subproceso A\] locale::global se establece en "Francés\_Francia.1252"**  
**\[Thread B\] Per\-thread locale is NOT enabled.**  
**\[Subproceso B\] La configuración regional de CRT se establece en "C"**  
**\[Subproceso B\] locale::global se establece en "Francés\_Francia.1252"**  
**\[Thread main\] Per\-thread locale is NOT enabled.**  
**\[Subproceso principal\] La configuración regional de CRT se establece en "C"**  
**\[Subproceso principal\] locale::global se establece en "Francés\_Francia.1252"**   
## Ejemplo  
 En este ejemplo, el subproceso principal genera dos subprocesos secundarios.  El primer subproceso, el subproceso A, habilita la configuración regional para cada subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`.  El segundo subproceso, el subproceso B, así como el subproceso principal, no habilitan la configuración regional para cada subproceso.  A continuación, el subproceso B procede a cambiar la configuración regional mediante la función [setlocale](../preprocessor/setlocale.md) de la Biblioteca en tiempo de ejecución de C.  
  
 Como el subproceso B no tiene habilitada la configuración regional para cada subproceso, las funciones de la Biblioteca en tiempo de ejecución de C del subproceso B y del subproceso principal empezarán a utilizar la configuración regional "francesa".  Las funciones de la Biblioteca en tiempo de ejecución de C del subproceso A continuarán utilizando la configuración regional de "C" porque el subproceso A tiene habilitada la configuración regional para cada subproceso.  A su vez, como [setlocale](../preprocessor/setlocale.md) no afecta a la configuración regional de la Biblioteca estándar de C\+\+, todos los objetos de ésta seguirán utilizando la configuración regional de "C".  
  
```  
// multithread_locale_3.cpp  
// compile with: /EHsc /MD  
#include <clocale>  
#include <cstdio>  
#include <locale>  
#include <process.h>  
#include <windows.h>  
  
#define NUM_THREADS 2  
using namespace std;  
  
unsigned __stdcall RunThreadA(void *params);  
unsigned __stdcall RunThreadB(void *params);  
  
BOOL localeSet = FALSE;  
BOOL configThreadLocaleCalled = FALSE;  
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);  
  
int main()  
{  
    HANDLE threads[NUM_THREADS];  
  
    unsigned aID;  
    threads[0] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadA, NULL, 0, &aID);  
  
    unsigned bID;  
    threads[1] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadB, NULL, 0, &bID);  
  
    WaitForMultipleObjects(2, threads, TRUE, INFINITE);  
  
    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread main] locale::global is set to \"%s\"\n",  
        locale().name().c_str());  
  
    CloseHandle(threads[0]);  
    CloseHandle(threads[1]);  
    CloseHandle(printMutex);  
  
    return 0;  
}  
  
unsigned __stdcall RunThreadA(void *params)  
{  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
    configThreadLocaleCalled = TRUE;  
    while (!localeSet)  
        Sleep(100);  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread A] Per-thread locale is enabled.\n");  
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
  
unsigned __stdcall RunThreadB(void *params)  
{  
    while (!configThreadLocaleCalled)  
        Sleep(100);  
    setlocale(LC_ALL, "french");  
    localeSet = TRUE;  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
```  
  
  **\[Thread B\] Per\-thread locale is NOT enabled.**  
**\[Subproceso B\] La configuración regional de CRT se establece en"Francés\_Francia.1252"**  
**\[Subproceso B\] configuración regional::global se establece en "C"**  
**\[Thread A\] Per\-thread locale is enabled.**  
**\[Subproceso A\] La configuración regional de CRT se establece en "C"**  
**\[Subproceso A\] locale::global se establece en "C"**  
**\[Thread main\] Per\-thread locale is NOT enabled.**  
**\[Subproceso principal\] La configuración regional de CRT se establece en"Francés\_Francia.1252"**  
**\[Subproceso principal\] locale::global se establece en "C"**   
## Ejemplo  
 En este ejemplo, el subproceso principal genera dos subprocesos secundarios.  El primer subproceso, el subproceso A, habilita la configuración regional para cada subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`.  El segundo subproceso, el subproceso B, así como el subproceso principal, no habilitan la configuración regional para cada subproceso.  A continuación, el subproceso B procede a cambiar la configuración regional mediante el método [locale::global](../Topic/locale::global.md) de la Biblioteca estándar de C\+\+.  
  
 Como el subproceso B no tiene habilitada la configuración regional para cada subproceso, las funciones de la Biblioteca en tiempo de ejecución de C del subproceso B y del subproceso principal empezarán a utilizar la configuración regional "francesa".  Las funciones de la Biblioteca en tiempo de ejecución de C del subproceso A continuarán utilizando la configuración regional de "C" porque el subproceso A tiene habilitada la configuración regional para cada subproceso.  Sin embargo, debido a que el método [locale::global](../Topic/locale::global.md) cambia "globalmente" la configuración regional, todos los objetos de la Biblioteca estándar de C\+\+ en todos los subprocesos empezarán a utilizar la configuración regional "francesa".  
  
```  
// multithread_locale_4.cpp  
// compile with: /EHsc /MD  
#include <clocale>  
#include <cstdio>  
#include <locale>  
#include <process.h>  
#include <windows.h>  
  
#define NUM_THREADS 2  
using namespace std;  
  
unsigned __stdcall RunThreadA(void *params);  
unsigned __stdcall RunThreadB(void *params);  
  
BOOL localeSet = FALSE;  
BOOL configThreadLocaleCalled = FALSE;  
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);  
  
int main()  
{  
    HANDLE threads[NUM_THREADS];  
  
    unsigned aID;  
    threads[0] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadA, NULL, 0, &aID);  
  
    unsigned bID;  
    threads[1] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadB, NULL, 0, &bID);  
  
    WaitForMultipleObjects(2, threads, TRUE, INFINITE);  
  
    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread main] locale::global is set to \"%s\"\n",  
        locale().name().c_str());  
  
    CloseHandle(threads[0]);  
    CloseHandle(threads[1]);  
    CloseHandle(printMutex);  
  
    return 0;  
}  
  
unsigned __stdcall RunThreadA(void *params)  
{  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
    configThreadLocaleCalled = TRUE;  
    while (!localeSet)  
        Sleep(100);  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread A] Per-thread locale is enabled.\n");  
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
  
unsigned __stdcall RunThreadB(void *params)  
{  
    while (!configThreadLocaleCalled)  
        Sleep(100);  
    locale::global(locale("french"));  
    localeSet = TRUE;  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
```  
  
  **\[Thread B\] Per\-thread locale is NOT enabled.**  
**\[Subproceso B\] La configuración regional de CRT se establece en"Francés\_Francia.1252"**  
**\[Subproceso B\] locale::global se establece en "Francés\_Francia.1252"**  
**\[Thread A\] Per\-thread locale is enabled.**  
**\[Subproceso A\] La configuración regional de CRT se establece en "C"**  
**\[Subproceso A\] locale::global se establece en "Francés\_Francia.1252"**  
**\[Thread main\] Per\-thread locale is NOT enabled.**  
**\[Subproceso principal\] La configuración regional de CRT se establece en"Francés\_Francia.1252"**  
**\[Subproceso principal\] locale::global se establece en "Francés\_Francia.1252"**   
## Vea también  
 [Compatibilidad del código antiguo con multithreading \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [\_beginthread, \_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../preprocessor/setlocale.md)   
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Configuración regional](../c-runtime-library/locale.md)   
 [\<clocale\>](../standard-library/clocale.md)   
 [\<locale\>](../standard-library/locale.md)   
 [locale \(Clase\)](../standard-library/locale-class.md)