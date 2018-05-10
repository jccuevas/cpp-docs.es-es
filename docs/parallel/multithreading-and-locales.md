---
title: Subprocesamiento múltiple y configuraciones regionales | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19cc3817faab71c209586ad952162229f846e0a7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-and-locales"></a>Subprocesamiento múltiple y configuraciones regionales
La biblioteca en tiempo de ejecución de C y la biblioteca estándar de C++ proporcionan compatibilidad para cambiar la configuración regional del programa. Este tema describen los problemas que surgen al utilizar la funcionalidad de configuración regional de las dos bibliotecas en una aplicación multiproceso.  
  
## <a name="remarks"></a>Comentarios  
 Con la biblioteca en tiempo de ejecución de C, puede crear aplicaciones multiproceso con la `_beginthread` y `_beginthreadex` funciones. En este tema solo cubre las aplicaciones multiproceso creadas mediante estas funciones. Para obtener más información, consulte [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
 Para cambiar la configuración regional mediante la biblioteca en tiempo de ejecución de C, use la [setlocale](../preprocessor/setlocale.md) función. En versiones anteriores de Visual C++, esta función siempre pueda modificar la configuración regional a lo largo de toda la aplicación. Ahora existe compatibilidad para establecer la configuración regional por subproceso. Esto se realiza mediante la [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) función. Para especificar que [setlocale](../preprocessor/setlocale.md) sólo debe cambiar la configuración regional en el subproceso actual, llamada `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` en ese subproceso. Por el contrario, una llamada a `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` hará que ese subproceso que se utilizan la configuración regional global y las llamadas a [setlocale](../preprocessor/setlocale.md) en que el subproceso cambiará la configuración regional de todos los subprocesos que no se ha habilitado explícitamente la configuración regional por subproceso.  
  
 Para cambiar la configuración regional mediante la biblioteca en tiempo de ejecución de C++, use la [locale (clase)](../standard-library/locale-class.md). Mediante una llamada a la [Locale:: global](../standard-library/locale-class.md#global) método, se cambiará la configuración regional de cada subproceso que no habilitó explícitamente la configuración regional por subproceso. Para cambiar la configuración regional de un único subproceso o parte de una aplicación, basta con crear una instancia de un `locale` objeto en dicho subproceso o parte del código.  
  
> [!NOTE]
>  Al llamar a [Locale:: global](../standard-library/locale-class.md#global) cambia la configuración regional para la biblioteca estándar de C++ y la biblioteca de C en tiempo de ejecución. Sin embargo, al llamar a [setlocale](../preprocessor/setlocale.md) solo cambia la configuración regional de la biblioteca en tiempo de ejecución de C; la biblioteca estándar de C++ no se verán afectadas.  
  
 Los ejemplos siguientes muestran cómo utilizar el [setlocale](../preprocessor/setlocale.md) función, el [locale (clase)](../standard-library/locale-class.md)y el [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) función puede cambiar la configuración regional de una aplicación en los diferentes escenarios.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, el subproceso principal genera dos subprocesos secundarios. El primer subproceso, el subproceso A, habilita la configuración regional por subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. El segundo subproceso, el subproceso B, así como el subproceso principal, no habilite la configuración regional por subproceso. Subproceso un, a continuación, procede a cambiar la configuración regional mediante la [setlocale](../preprocessor/setlocale.md) función de la biblioteca de C en tiempo de ejecución.  
  
 Puesto que un subproceso tiene regional para cada subproceso está habilitada, solo las funciones de biblioteca en tiempo de ejecución de C en el subproceso A empezarán a utilizar la configuración regional "francesa". Las funciones de biblioteca en tiempo de ejecución de C en el subproceso B y en el subproceso principal continuarán utilizando la configuración regional "C". Además, dado que [setlocale](../preprocessor/setlocale.md) no afecta a la configuración regional de la biblioteca estándar de C++, biblioteca estándar de C++ todos los objetos seguirán utilizando la configuración regional "C".  
  
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
  
```Output  
[Thread A] Per-thread locale is enabled.  
[Thread A] CRT locale is set to "French_France.1252"  
[Thread A] locale::global is set to "C"  
  
[Thread B] Per-thread locale is NOT enabled.  
[Thread B] CRT locale is set to "C"  
[Thread B] locale::global is set to "C"  
  
[Thread main] Per-thread locale is NOT enabled.  
[Thread main] CRT locale is set to "C"  
[Thread main] locale::global is set to "C"  
```  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, el subproceso principal genera dos subprocesos secundarios. El primer subproceso, el subproceso A, habilita la configuración regional por subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. El segundo subproceso, el subproceso B, así como el subproceso principal, no habilite la configuración regional por subproceso. Subproceso un, a continuación, procede a cambiar la configuración regional mediante la [Locale:: global](../standard-library/locale-class.md#global) método de la biblioteca estándar de C++.  
  
 Puesto que un subproceso tiene regional para cada subproceso está habilitada, solo las funciones de biblioteca en tiempo de ejecución de C en el subproceso A empezarán a utilizar la configuración regional "francesa". Las funciones de biblioteca en tiempo de ejecución de C en el subproceso B y en el subproceso principal continuarán utilizando la configuración regional "C". Sin embargo, dado que la [Locale:: global](../standard-library/locale-class.md#global) método cambia la configuración regional "global", todos los objetos de la biblioteca estándar de C++ en todos los subprocesos empezar a usar la configuración regional "francesa".  
  
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
  
```Output  
[Thread A] Per-thread locale is enabled.  
[Thread A] CRT locale is set to "French_France.1252"  
[Thread A] locale::global is set to "French_France.1252"  
  
[Thread B] Per-thread locale is NOT enabled.  
[Thread B] CRT locale is set to "C"  
[Thread B] locale::global is set to "French_France.1252"  
  
[Thread main] Per-thread locale is NOT enabled.  
[Thread main] CRT locale is set to "C"  
[Thread main] locale::global is set to "French_France.1252"  
```  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, el subproceso principal genera dos subprocesos secundarios. El primer subproceso, el subproceso A, habilita la configuración regional por subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. El segundo subproceso, el subproceso B, así como el subproceso principal, no habilite la configuración regional por subproceso. Continuación, el subproceso B procede a cambiar la configuración regional mediante la [setlocale](../preprocessor/setlocale.md) función de la biblioteca de C en tiempo de ejecución.  
  
 Puesto que el subproceso B no tiene habilitada la configuración regional por subproceso, las funciones de biblioteca en tiempo de ejecución de C en el subproceso B y en el subproceso principal empezar a usar la configuración regional "francesa". Las funciones de biblioteca en tiempo de ejecución de C en continuar con el subproceso A usar la configuración regional "C" porque el subproceso A tiene habilitada la configuración regional por subproceso. Además, dado que [setlocale](../preprocessor/setlocale.md) no afecta a la configuración regional de la biblioteca estándar de C++, biblioteca estándar de C++ todos los objetos seguirán utilizando la configuración regional "C".  
  
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
  
```Output  
[Thread B] Per-thread locale is NOT enabled.  
[Thread B] CRT locale is set to "French_France.1252"  
[Thread B] locale::global is set to "C"  
  
[Thread A] Per-thread locale is enabled.  
[Thread A] CRT locale is set to "C"  
[Thread A] locale::global is set to "C"  
  
[Thread main] Per-thread locale is NOT enabled.  
[Thread main] CRT locale is set to "French_France.1252"  
[Thread main] locale::global is set to "C"  
```  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, el subproceso principal genera dos subprocesos secundarios. El primer subproceso, el subproceso A, habilita la configuración regional por subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. El segundo subproceso, el subproceso B, así como el subproceso principal, no habilite la configuración regional por subproceso. Continuación, el subproceso B procede a cambiar la configuración regional mediante la [Locale:: global](../standard-library/locale-class.md#global) método de la biblioteca estándar de C++.  
  
 Puesto que el subproceso B no tiene habilitada la configuración regional por subproceso, las funciones de biblioteca en tiempo de ejecución de C en el subproceso B y en el subproceso principal empezar a usar la configuración regional "francesa". Las funciones de biblioteca en tiempo de ejecución de C en continuar con el subproceso A usar la configuración regional "C" porque el subproceso A tiene habilitada la configuración regional por subproceso. Sin embargo, dado que la [Locale:: global](../standard-library/locale-class.md#global) método cambia la configuración regional "global", todos los objetos de la biblioteca estándar de C++ en todos los subprocesos empezar a usar la configuración regional "francesa".  
  
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
  
```Output  
[Thread B] Per-thread locale is NOT enabled.  
[Thread B] CRT locale is set to "French_France.1252"  
[Thread B] locale::global is set to "French_France.1252"  
  
[Thread A] Per-thread locale is enabled.  
[Thread A] CRT locale is set to "C"  
[Thread A] locale::global is set to "French_France.1252"  
  
[Thread main] Per-thread locale is NOT enabled.  
[Thread main] CRT locale is set to "French_France.1252"  
[Thread main] locale::global is set to "French_France.1252"  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con multithreading código antiguo (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../preprocessor/setlocale.md)   
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Configuración regional](../c-runtime-library/locale.md)   
 [\<clocale >](../standard-library/clocale.md)   
 [\<locale>](../standard-library/locale.md)   
 [locale (Clase)](../standard-library/locale-class.md)