---
title: _beginthread, _beginthreadex | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8e12e25f64972335cb1a1199ae519de71d43067
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="beginthread-beginthreadex"></a>_beginthread, _beginthreadex

Crea un subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
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

### <a name="parameters"></a>Parámetros

*start_address*<br/>
Dirección de inicio de una rutina que comienza la ejecución de un nuevo subproceso. Para **_beginthread**, la convención de llamada es [__cdecl](../../cpp/cdecl.md) (para código nativo) o [__clrcall](../../cpp/clrcall.md) (para código administrado); para **_beginthreadex**, está [__stdcall](../../cpp/stdcall.md) (para código nativo) o [__clrcall](../../cpp/clrcall.md) (para código administrado).

*stack_size*<br/>
Tamaño de la pila de un subproceso nuevo, o 0.

*arglist*<br/>
Lista de argumentos que se pasan a un nuevo subproceso, o **NULL**.

*Seguridad*<br/>
Puntero a una estructura de [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) que determina si el identificador devuelto se puede heredar de procesos secundarios. Si *seguridad* es **NULL**, el identificador no puede heredarse. Debe ser **NULL** para aplicaciones de Windows 95.

*initflag*<br/>
Marcas que controlan el estado inicial de un nuevo subproceso. Establecer *initflag* en 0 para que se ejecute inmediatamente o en **CREATE_SUSPENDED** para crear el subproceso en un estado suspendido; use [ResumeThread](http://msdn.microsoft.com/library/windows/desktop/ms685086.aspx) para ejecutar el subproceso. Establecer *initflag* a **STACK_SIZE_PARAM_IS_A_RESERVATION** marca para usar *stack_size* como inicial reservar el tamaño de la pila en bytes; si es esta marca no se especifica, *stack_size* especifica el tamaño de confirmación.

*thrdaddr*<br/>
Señala a una variable de 32 bits que recibe el identificador del subproceso. Si es **NULL**, no se utiliza.

## <a name="return-value"></a>Valor devuelto

Si es correcto, cada una de estas funciones devuelve un identificador al subproceso recién creado; Sin embargo, si el subproceso recién creado sale demasiado rápido, **_beginthread** no puede devolver un identificador válido. (Vea la explicación en la sección Comentarios). Produce un error, **_beginthread** devuelve-1 L y **errno** está establecido en **EAGAIN** si hay demasiados subprocesos, en **EINVAL** si el argumento es no válido o el tamaño de pila es incorrecto, o a **EACCES** si no hay suficientes recursos (como memoria). Produce un error, **_beginthreadex** devuelve 0, y **errno** y **_doserrno** están establecidos.

Si *start_address* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devuelven -1.

Para obtener más información sobre estos y otros códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener más información acerca de **uintptr_t**, consulte [tipos estándar](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Comentarios

El **_beginthread** función crea un subproceso que comienza la ejecución de una rutina en *start_address*. La rutina en *start_address* debe utilizar el **__cdecl** (para código nativo) o **__clrcall** (para código administrado) convención de llamada y no debe tener ningún valor devuelto. Cuando el subproceso vuelve de la rutina, finaliza automáticamente. Para obtener más información sobre los subprocesos, consulte [Compatibilidad del código antiguo con multithreading (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** es similar a la de Win32 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453.aspx) API más estrechamente a **_beginthread** does. **_beginthreadex** difiere de **_beginthread** de las maneras siguientes:

- **_beginthreadex** tiene tres parámetros adicionales: *initflag*, *seguridad*, y **threadaddr**. El nuevo subproceso pueden crearse en un estado suspendido, con una seguridad especificada y puede obtenerse mediante el uso de *thrdaddr*, que es el identificador del subproceso.

- La rutina en *start_address* que se pasa a **_beginthreadex** debe utilizar el **__stdcall** (para código nativo) o **__clrcall** (para código administrado) convención de llamada y debe devolver un código de salida del subproceso.

- **_beginthreadex** devuelve 0 en el error, en lugar de-1 L.

- Un subproceso que se crea mediante **_beginthreadex** termina con una llamada a [_endthreadex](endthread-endthreadex.md).

El **_beginthreadex** función ofrece un mayor control sobre cómo se crea el subproceso que **_beginthread** does. El **_endthreadex** función también es más flexible. Por ejemplo, con **_beginthreadex**, puede utilizar la información de seguridad, establecer el estado inicial del subproceso (en ejecución o suspendido) y obtener el identificador de subproceso del subproceso creado recientemente. También puede utilizar el identificador de subproceso devuelto por **_beginthreadex** con la sincronización API, lo que no se puede realizar con **_beginthread**.

Es más seguro usar **_beginthreadex** de **_beginthread**. Si el subproceso que genera **_beginthread** sale rápidamente, el identificador que se devuelve al llamador del **_beginthread** podría no ser válido o señalar a otro subproceso. Sin embargo, el identificador devuelto por **_beginthreadex** tiene que estar cerrado por el autor de llamada de **_beginthreadex**, por lo que se garantiza que sea un identificador válido si **_beginthreadex** no se ha devuelto un error.

Puede llamar a [_endthread](endthread-endthreadex.md) o **_endthreadex** explícitamente para terminar un subproceso; sin embargo, **_endthread** o **_endthreadex** se llama automáticamente cuando el subproceso vuelve de la rutina que se pasa como un parámetro. Finaliza un subproceso con una llamada a **_endthread** o **_endthreadex** ayuda a garantiza la recuperación correcta de recursos que se asignan para el subproceso.

**_endthread** cierra automáticamente el identificador de subproceso, mientras que **_endthreadex** no lo hace. Por lo tanto, cuando usa **_beginthread** y **_endthread**, no cierre explícitamente el identificador de subproceso mediante una llamada a Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) API. Este comportamiento difiere de la API [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) de Win32.

> [!NOTE]
> Para un archivo ejecutable vinculado con Libcmt.lib, no llame a Win32 **ExitThread** API por lo que no impiden que el sistema en tiempo de ejecución reclame los recursos asignados. **_endthread** y **_endthreadex** reclamar los recursos de subprocesos asignados y, a continuación, llame a **ExitThread**.

El sistema operativo controla la asignación de la pila cuando cualquier **_beginthread** o **_beginthreadex** se denomina; no tiene que pasar la dirección de la pila del subproceso a ninguna de estas funciones. Además, el *stack_size* argumento puede ser 0, en cuyo caso el sistema operativo utiliza el mismo valor que la pila que se especifica para el subproceso principal.

*arglist* es un parámetro que se pasa al subproceso recién creado. Normalmente, es la dirección de un elemento de datos, como una cadena de caracteres. *arglist* puede ser **NULL** si no es necesaria, pero **_beginthread** y **_beginthreadex** se debe proporcionar algún valor para pasar al nuevo subproceso. Se terminan todos los subprocesos si cualquier subproceso llama [anular](abort.md), **salir**, **_exit**, o **ExitProcess**.

La configuración regional del nuevo subproceso se inicializa con la información de configuración regional de actual global por proceso. Si está habilitada la configuración regional por subproceso mediante una llamada a [_configthreadlocale](configthreadlocale.md) (tanto globalmente como para nuevos subprocesos solamente), el subproceso puede cambiar su configuración regional independientemente de otros subprocesos mediante una llamada a **setlocale** o **_wsetlocale**. Subprocesos que no tienen el indicador de configuración regional por subproceso establece pueden afectar a la información de configuración regional en todos los demás subprocesos que tampoco tiene el indicador de configuración regional por subproceso establecido, así como todos los subprocesos recién creado. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Para código mixto y puro, **_beginthread** y **_beginthreadex** tienen dos sobrecargas. Una toma un puntero a función de convención de llamada nativa y la otra toma un **__clrcall** puntero de función. La primera sobrecarga no es una aplicación de dominio seguro y nunca lo será. Si está escribiendo código mixto o puro, debe asegurarse de que el nuevo subproceso entra en el dominio de aplicación correcto antes de tener acceso a recursos administrados. Para ello, por ejemplo, use [call_in_appdomain (Función)](../../dotnet/call-in-appdomain-function.md). La segunda sobrecarga es una aplicación de dominio seguro; el subproceso recién creado finalizará siempre en el dominio de aplicación del autor de la llamada de **_beginthread** o **_beginthreadex**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo las versiones de multiproceso de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md) .

Usar **_beginthread** o **_beginthreadex**, la aplicación debe vincularse a una de las bibliotecas de tiempo de ejecución de C multiproceso.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se utiliza **_beginthread** y **_endthread**.

```C
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

El código de ejemplo siguiente muestra cómo puede utilizar el identificador de subproceso devuelto por **_beginthreadex** con la API de sincronización [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx). El subproceso principal espera que el segundo subproceso finalice antes de continuar. Cuando el segundo subproceso llama **_endthreadex**, hace que el objeto de subproceso hacia el estado señalado. Esto permite que el subproceso principal continúe ejecutándose. Esto no es posible con **_beginthread** y **_endthread**, porque **_endthread** llamadas **CloseHandle**, que destruye el subproceso objeto antes de que se puede establecer en el estado señalado.

```cpp
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

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_endthread, _endthreadex](endthread-endthreadex.md)<br/>
[abort](abort.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)<br/>
