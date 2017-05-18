---
title: _beginthread, _beginthreadex | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _beginthread
- _beginthreadex
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
dev_langs:
- C++
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
caps.latest.revision: 36
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 3c556e6460f1a39bab23f2612cbf820e284d7605
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="beginthread-beginthreadex"></a>_beginthread, _beginthreadex
Crea un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
uintptr_t _beginthread( // NATIVE CODE  
   void( __cdecl *start_address )( void * ),  
   unsigned stack_size,  
   void *arglist   
);  
uintptr_t _beginthread( // MANAGED CODE  
   void( __clrcall *start_address )( void * ),  
   unsigned stack_size,  
   void *arglist   
);  
uintptr_t _beginthreadex( // NATIVE CODE  
   void *security,  
   unsigned stack_size,  
   unsigned ( __stdcall *start_address )( void * ),  
   void *arglist,  
   unsigned initflag,  
   unsigned *thrdaddr   
);  
uintptr_t _beginthreadex( // MANAGED CODE  
   void *security,  
   unsigned stack_size,  
   unsigned ( __clrcall *start_address )( void * ),  
   void *arglist,  
   unsigned initflag,  
   unsigned *thrdaddr   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `start_address`  
 Dirección de inicio de una rutina que comienza la ejecución de un nuevo subproceso. Para `_beginthread`, la convención de llamada es [__cdecl](../../cpp/cdecl.md) (para código nativo) o [__clrcall](../../cpp/clrcall.md) (para código administrado); para `_beginthreadex`, es [__stdcall](../../cpp/stdcall.md) (para código nativo) o [__clrcall](../../cpp/clrcall.md) (para código administrado).  
  
 `stack_size`  
 Tamaño de la pila de un subproceso nuevo, o 0.  
  
 `arglist`  
 Lista de argumentos que se van a pasar a un nuevo subproceso, o NULL.  
  
 `Security`  
 Puntero a una estructura de [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) que determina si el identificador devuelto se puede heredar de procesos secundarios. Si `Security` es NULL, el identificador no puede heredarse. Debe ser NULL para aplicaciones de Windows 95.  
  
 `initflag`  
 Marcas que controlan el estado inicial de un nuevo subproceso. Establezca `initflag` en `0` para que se ejecute inmediatamente o en `CREATE_SUSPENDED` para crear el subproceso en estado suspendido. Use [ResumeThread](http://msdn.microsoft.com/library/windows/desktop/ms685086.aspx) para ejecutar el subproceso. Establezca `initflag` en la marca `STACK_SIZE_PARAM_IS_A_RESERVATION` para que use `stack_size` como tamaño de reserva inicial de la pila en bytes; si esta marca no se especifica, `stack_size` determinará el tamaño confirmado.  
  
 `thrdaddr`  
 Señala a una variable de 32 bits que recibe el identificador del subproceso. Si es NULL, no se utiliza.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, cada una de estas funciones devuelve un identificador al subproceso creado recientemente; sin embargo, si el subproceso recién creado sale demasiado rápido, `_beginthread` no puede devolver un identificador válido. (Vea la explicación en la sección Comentarios). En un error, `_beginthread` devuelve -1L y `errno` se establece en `EAGAIN` si hay demasiados subprocesos, en `EINVAL` si el argumento no es válido o el tamaño de pila es incorrecto, o en `EACCES` si hay recursos insuficientes (como memoria). En un error, `_beginthreadex` devuelve 0 y se establecen `errno` y `_doserrno` .  
  
 Si `startaddress` es NULL, se invoca el controlador de parámetros no válidos, tal y como se describe en [Parameter Validation](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven -1.  
  
 Para obtener más información sobre estos y otros códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener más información sobre `uintptr_t`, consulte [Tipos estándar](../../c-runtime-library/standard-types.md).  
  
## <a name="remarks"></a>Comentarios  
 La función de `_beginthread` crea un subproceso que comienza la ejecución de una rutina en `start_address`. La rutina en `start_address` debe utilizar la convención de llamada `__cdecl` (para código nativo) o `__clrcall` (para código administrado) y no debe tener ningún valor devuelto. Cuando el subproceso vuelve de la rutina, finaliza automáticamente. Para obtener más información sobre los subprocesos, consulte [Compatibilidad del código antiguo con multithreading (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 `_beginthreadex` se parece más a la API [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453.aspx) de Win32 que `_beginthread`. `_beginthreadex` se diferencia de `_beginthread` de las maneras siguientes:  
  
-   `_beginthreadex` tiene tres parámetros adicionales: `initflag`, `security`y `threadaddr`. El nuevo subproceso se puede crear en un estado suspendido, con una seguridad especificada, y se puede acceder a él por medio de `thrdaddr`, que es el identificador del subproceso.  
  
-   La rutina en `start_address` que se pasa a `_beginthreadex` debe utilizar la convención de llamada `__stdcall` (para código nativo) o `__clrcall` (para código administrado) y debe devolver un código de salida del subproceso.  
  
-   `_beginthreadex` devuelve 0 en el error, en lugar de -1L.  
  
-   Un subproceso que se crea mediante `_beginthreadex` termina con una llamada a [_endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md).  
  
 La función de `_beginthreadex` le ofrece más control sobre cómo se crea el subproceso que hace `_beginthread` . La función de `_endthreadex` también es más flexible. Por ejemplo, con `_beginthreadex`, puede usar la información de seguridad, establecer el estado inicial del subproceso (en ejecución o en suspensión) y obtener el identificador del subproceso del subproceso creado recientemente. También puede utilizar el identificador de subproceso devuelto por `_beginthreadex` con la sincronización API, lo que no puede realizar con `_beginthread`.  
  
 Es más seguro utilizar `_beginthreadex` que `_beginthread`. Si el subproceso que genera `_beginthread` sale rápidamente, el identificador que se devuelve al llamador de `_beginthread` podría ser no válido o señalar a otro subproceso. Sin embargo, el identificador devuelto por `_beginthreadex` tiene que cerrar el llamador de `_beginthreadex`, por lo que se garantiza que sea un identificador válido si `_beginthreadex` no devuelve un error.  
  
 Puede llamar a [_endthread](../../c-runtime-library/reference/endthread-endthreadex.md) o `_endthreadex` explícitamente para terminar el subproceso; sin embargo, se llama a `_endthread` o `_endthreadex` automáticamente cuando el subproceso vuelve de la rutina que se pasa como parámetro. Si se finaliza un subproceso con una llamada a `_endthread` o las ayudas de `_endthreadex` , se garantiza la recuperación correcta de los recursos que se asignan para el subproceso.  
  
 `_endthread` automáticamente cierra el identificador de subproceso, aunque `_endthreadex` no lo hace. Por consiguiente, cuando use `_beginthread` y `_endthread`, no cierre el identificador de subproceso de forma explícita llamando a la API [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) de Win32. Este comportamiento difiere de la API [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) de Win32.  
  
> [!NOTE]
>  Para un archivo ejecutable vinculado con Libcmt.lib, no llame a la API `ExitThread` Win32 a fin de no impedir que el sistema en tiempo de ejecución reclame los recursos asignados. `_endthread` y `_endthreadex` recuperan los recursos de subprocesos asignados y después llaman a `ExitThread`.  
  
 El sistema operativo controla la asignación de la pila cuando se llama a `_beginthread` o `_beginthreadex` ; no tiene que pasar la dirección de la pila del subproceso a ninguna de estas funciones. Además, el argumento de `stack_size` puede ser 0, en cuyo caso el sistema operativo utiliza el mismo valor que la pila que se especifica para el subproceso principal.  
  
 `arglist` es un parámetro que se pasará al subproceso recién creado. Normalmente, es la dirección de un elemento de datos, como una cadena de caracteres. `arglist` puede ser NULL si no se necesita, pero se debe dar al menos un valor a `_beginthread` y `_beginthreadex` para pasar al nuevo subproceso. Se terminan todos los subprocesos si cualquier subproceso llama a `abort`, `exit`, `_exit`o `ExitProcess`.  
  
 La configuración regional del nuevo subproceso se hereda del subproceso primario. Si la configuración regional para cada subproceso está habilitada por una llamada a [_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md) (tanto globalmente como para nuevos subprocesos solamente), el subproceso puede cambiar su configuración regional independientemente de su elemento primario llamando a `setlocale` o `_wsetlocale`. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).  
  
 Para código mixto y puro, `_beginthread` y `_beginthreadex` tienen dos sobrecargas: una toma un puntero a función de convención nativa de llamadas, mientras que la otra toma un puntero a función de `__clrcall` . La primera sobrecarga no es una aplicación de dominio seguro y nunca lo será. Si está escribiendo código mixto o puro, debe asegurarse de que el nuevo subproceso entra en el dominio de aplicación correcto antes de tener acceso a recursos administrados. Para ello, por ejemplo, use [call_in_appdomain (Función)](../../dotnet/call-in-appdomain-function.md). La segunda sobrecarga es una aplicación de dominio seguro; el subproceso recién creado finalizará siempre en el dominio de aplicación del llamador de `_beginthread` o de `_beginthreadex`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_beginthread`|\<process.h>|  
|`_beginthreadex`|\<process.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Solo las versiones de multiproceso de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md) .  
  
 Para utilizar `_beginthread` o `_beginthreadex`, la aplicación debe vincularse a una de las bibliotecas en tiempo de ejecución multiproceso de C.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza `_beginthread` y `_endthread`.  
  
```  
// crt_BEGTHRD.C  
// compile with: /MT /D "_X86_" /c  
// processor: x86  
#include <windows.h>  
#include <process.h>    /* _beginthread, _endthread */  
#include <stddef.h>  
#include <stdlib.h>  
#include <conio.h>  
  
void Bounce( void * );  
void CheckKey( void * );  
  
// GetRandom returns a random integer between min and max.  
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))  
// GetGlyph returns a printable ASCII character value  
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))  
  
BOOL repeat = TRUE;                 // Global repeat flag   
HANDLE hStdOut;                     // Handle for console window  
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure  
  
int main()  
{  
    int param = 0;  
    int * pparam = &param;  
  
    // Get display screen's text row and column information.  
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );  
    GetConsoleScreenBufferInfo( hStdOut, &csbi );  
  
    // Launch CheckKey thread to check for terminating keystroke.  
    _beginthread( CheckKey, 0, NULL );  
  
    // Loop until CheckKey terminates program or 1000 threads created.   
    while( repeat && param < 1000 )  
    {  
        // launch another character thread.  
        _beginthread( Bounce, 0, (void *) pparam );  
  
        // increment the thread parameter  
        param++;  
  
        // Wait one second between loops.  
        Sleep( 1000L );  
    }  
}  
  
// CheckKey - Thread to wait for a keystroke, then clear repeat flag.  
void CheckKey( void * ignored )  
{  
    _getch();  
    repeat = 0;    // _endthread implied  
}  
  
// Bounce - Thread to create and and control a colored letter that moves  
// around on the screen.  
//  
// Params: parg - the value to create the character from  
void Bounce( void * parg )  
{  
    char       blankcell = 0x20;  
    CHAR_INFO  ci;  
    COORD      oldcoord, cellsize, origin;  
    DWORD      result;  
    SMALL_RECT region;  
  
    cellsize.X = cellsize.Y = 1;  
    origin.X = origin.Y = 0;  
  
    // Generate location, letter and color attribute from thread argument.  
    srand( _threadid );  
    oldcoord.X = region.Left = region.Right =   
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);  
    oldcoord.Y = region.Top = region.Bottom =   
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);  
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));  
    ci.Attributes = GetRandom(1, 15);  
  
    while (repeat)  
    {  
        // Pause between loops.  
        Sleep( 100L );  
  
        // Blank out our old position on the screen, and draw new letter.  
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);  
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);  
  
        // Increment the coordinate for next placement of the block.  
        oldcoord.X = region.Left;  
        oldcoord.Y = region.Top;  
        region.Left = region.Right += GetRandom(-1, 1);  
        region.Top = region.Bottom += GetRandom(-1, 1);  
  
        // Correct placement (and beep) if about to go off the screen.  
        if (region.Left < csbi.srWindow.Left)  
            region.Left = region.Right = csbi.srWindow.Left + 1;  
        else if (region.Right >= csbi.srWindow.Right)  
            region.Left = region.Right = csbi.srWindow.Right - 2;  
        else if (region.Top < csbi.srWindow.Top)  
            region.Top = region.Bottom = csbi.srWindow.Top + 1;  
        else if (region.Bottom >= csbi.srWindow.Bottom)  
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;  
  
        // If not at a screen border, continue, otherwise beep.  
        else  
            continue;  
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);  
    }  
    // _endthread given to terminate  
    _endthread();  
}  
```  
  
 Presione cualquier tecla para finalizar la aplicación de ejemplo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo se puede usar el identificador de subproceso devuelto por `_beginthreadex` con la API de sincronización [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx). El subproceso principal espera que el segundo subproceso finalice antes de continuar. Cuando el segundo subproceso llama a `_endthreadex`, hace que el objeto del subproceso vaya al estado señalado. Esto permite que el subproceso principal continúe ejecutándose. Esto no se puede hacer con `_beginthread` y `_endthread`, porque `_endthread` llama a `CloseHandle`, que destruye el objeto de subproceso antes de poder establecerlo en el estado señalado.  
  
```  
// crt_begthrdex.cpp  
// compile with: /MT  
#include <windows.h>  
#include <stdio.h>  
#include <process.h>  
  
unsigned Counter;   
unsigned __stdcall SecondThreadFunc( void* pArguments )  
{  
    printf( "In second thread...\n" );  
  
    while ( Counter < 1000000 )  
        Counter++;  
  
    _endthreadex( 0 );  
    return 0;  
}   
  
int main()  
{   
    HANDLE hThread;  
    unsigned threadID;  
  
    printf( "Creating second thread...\n" );  
  
    // Create the second thread.  
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );  
  
    // Wait until second thread terminates. If you comment out the line  
    // below, Counter will not be correct because the thread has not  
    // terminated, and Counter most likely has not been incremented to  
    // 1000000 yet.  
    WaitForSingleObject( hThread, INFINITE );  
    printf( "Counter should be 1000000; it is-> %d\n", Counter );  
    // Destroy the thread object.  
    CloseHandle( hThread );  
}  
```  
  
```Output  
Creating second thread...  
In second thread...  
Counter should be 1000000; it is-> 1000000  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [_endthread, _endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)
