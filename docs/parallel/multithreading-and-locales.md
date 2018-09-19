---
title: Multithreading y configuraciones regionales | Microsoft Docs
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
ms.openlocfilehash: 1e6bef9e707636d18ed5ecb78098661a753111ba
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132186"
---
# <a name="multithreading-and-locales"></a>Subprocesamiento múltiple y configuraciones regionales
La biblioteca en tiempo de ejecución de C y la biblioteca estándar de C++ proporcionan compatibilidad para cambiar la configuración regional del programa. En este tema se describe los problemas que surgen al utilizar la funcionalidad de configuración regional de las dos bibliotecas en una aplicación multiproceso.  
  
## <a name="remarks"></a>Comentarios  

Con la biblioteca en tiempo de ejecución de C, puede crear aplicaciones multiproceso con el `_beginthread` y `_beginthreadex` funciones. En este tema solo cubre aplicaciones multiproceso con comportamiento creadas mediante estas funciones. Para obtener más información, consulte [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
Para cambiar la configuración regional mediante la biblioteca en tiempo de ejecución de C, use el [setlocale](../preprocessor/setlocale.md) función. En versiones anteriores de Visual C++, esta función siempre podría modificar la configuración regional en toda la aplicación. Ahora existe compatibilidad para establecer la configuración regional por subproceso. Esto se realiza mediante el [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) función. Para especificar que [setlocale](../preprocessor/setlocale.md) sólo debe cambiar la configuración regional en el subproceso actual, llamada `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` en ese subproceso. Por el contrario, una llamada a `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` hará que el subproceso para usar la configuración regional global y las llamadas a [setlocale](../preprocessor/setlocale.md) en que el subproceso cambiará la configuración regional en todos los subprocesos que no se ha habilitado explícitamente la configuración regional por subproceso.  
  
Para cambiar la configuración regional mediante la biblioteca en tiempo de ejecución de C++, use el [locale (clase)](../standard-library/locale-class.md). Mediante una llamada a la [Locale:: global](../standard-library/locale-class.md#global) método, cambia la configuración regional de cada subproceso que no se ha habilitado explícitamente la configuración regional por subproceso. Para cambiar la configuración regional en un único subproceso o parte de una aplicación, simplemente cree una instancia de un `locale` objeto en ese subproceso o parte del código.  
  
> [!NOTE]
> Una llamada a [Locale:: global](../standard-library/locale-class.md#global) cambia la configuración regional para la biblioteca estándar de C++ y la biblioteca de C en tiempo de ejecución. Sin embargo, una llamada a [setlocale](../preprocessor/setlocale.md) solo cambia la configuración regional para la biblioteca en tiempo de ejecución de C; la biblioteca estándar de C++ no se ve afectado.  
  
Los ejemplos siguientes muestran cómo usar el [setlocale](../preprocessor/setlocale.md) función, el [locale (clase)](../standard-library/locale-class.md)y el [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) función para cambiar la configuración regional de una aplicación en varios escenarios diferentes.  
  
## <a name="example"></a>Ejemplo  
 
En este ejemplo, el subproceso principal genera dos subprocesos secundarios. El primer subproceso, el subproceso A, habilita la configuración regional por subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. El segundo subproceso, el subproceso B, así como el subproceso principal, no habilite la configuración regional por subproceso. Subproceso después procede a cambiar la configuración regional mediante la [setlocale](../preprocessor/setlocale.md) función de la biblioteca de C en tiempo de ejecución.  
  
Puesto que un subproceso tiene regional para cada subproceso está habilitada, solo las funciones de biblioteca en tiempo de ejecución de C en el menú Inicio de un subproceso con la configuración regional "francés". Las funciones de biblioteca en tiempo de ejecución de C en el subproceso B y en el subproceso principal seguirán usando la configuración regional "C". Además, dado que [setlocale](../preprocessor/setlocale.md) no afecta a la configuración regional de la biblioteca estándar de C++, biblioteca estándar de C++ todos los objetos seguirán utilizando la configuración regional "C".  
  
```cpp  
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
 
En este ejemplo, el subproceso principal genera dos subprocesos secundarios. El primer subproceso, el subproceso A, habilita la configuración regional por subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. El segundo subproceso, el subproceso B, así como el subproceso principal, no habilite la configuración regional por subproceso. Subproceso después procede a cambiar la configuración regional mediante la [Locale:: global](../standard-library/locale-class.md#global) método de la biblioteca estándar de C++.  
  
Puesto que un subproceso tiene regional para cada subproceso está habilitada, solo las funciones de biblioteca en tiempo de ejecución de C en el menú Inicio de un subproceso con la configuración regional "francés". Las funciones de biblioteca en tiempo de ejecución de C en el subproceso B y en el subproceso principal seguirán usando la configuración regional "C". Sin embargo, dado que el [Locale:: global](../standard-library/locale-class.md#global) método cambia la configuración regional "global", todos los objetos de biblioteca estándar de C++ en todos los subprocesos empezar a usar la configuración regional "francés".  
  
```cpp  
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
 
En este ejemplo, el subproceso principal genera dos subprocesos secundarios. El primer subproceso, el subproceso A, habilita la configuración regional por subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. El segundo subproceso, el subproceso B, así como el subproceso principal, no habilite la configuración regional por subproceso. Subproceso B, a continuación, procede a cambiar la configuración regional mediante la [setlocale](../preprocessor/setlocale.md) función de la biblioteca de C en tiempo de ejecución.  
  
Puesto que el subproceso B no tiene habilitada la configuración regional por subproceso, las funciones de biblioteca en tiempo de ejecución de C en el subproceso B y en el subproceso principal empezar a usar la configuración regional "francés". Las funciones de biblioteca en tiempo de ejecución de C en pasar de un subproceso a utilizar la configuración regional "C" porque un subproceso tiene habilitada la configuración regional por subproceso. Además, dado que [setlocale](../preprocessor/setlocale.md) no afecta a la configuración regional de la biblioteca estándar de C++, biblioteca estándar de C++ todos los objetos seguirán utilizando la configuración regional "C".  
  
```cpp  
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
 
En este ejemplo, el subproceso principal genera dos subprocesos secundarios. El primer subproceso, el subproceso A, habilita la configuración regional por subproceso llamando a `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. El segundo subproceso, el subproceso B, así como el subproceso principal, no habilite la configuración regional por subproceso. Subproceso B, a continuación, procede a cambiar la configuración regional mediante la [Locale:: global](../standard-library/locale-class.md#global) método de la biblioteca estándar de C++.  
  
Puesto que el subproceso B no tiene habilitada la configuración regional por subproceso, las funciones de biblioteca en tiempo de ejecución de C en el subproceso B y en el subproceso principal empezar a usar la configuración regional "francés". Las funciones de biblioteca en tiempo de ejecución de C en pasar de un subproceso a utilizar la configuración regional "C" porque un subproceso tiene habilitada la configuración regional por subproceso. Sin embargo, dado que el [Locale:: global](../standard-library/locale-class.md#global) método cambia la configuración regional "global", todos los objetos de biblioteca estándar de C++ en todos los subprocesos empezar a usar la configuración regional "francés".  
  
```cpp  
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

[Compatibilidad con multithreading código antiguo (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)   
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)   
[setlocale](../preprocessor/setlocale.md)   
[Internacionalización](../c-runtime-library/internationalization.md)   
[Configuración regional](../c-runtime-library/locale.md)   
[\<clocale >](../standard-library/clocale.md)   
[\<locale>](../standard-library/locale.md)   
[locale (Clase)](../standard-library/locale-class.md)