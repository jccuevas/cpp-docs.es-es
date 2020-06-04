---
title: _beginthread, _beginthreadex
ms.date: 4/2/2020
api_name:
- _beginthread
- _beginthreadex
- _o__beginthread
- _o__beginthreadex
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: acf885c923db3fdf91119b29a78d64824384166b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913504"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread, _beginthreadex

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
Dirección de inicio de una rutina que comienza la ejecución de un nuevo subproceso. Por **_beginthread**, la Convención de llamada es [__cdecl](../../cpp/cdecl.md) (para código nativo) o [__clrcall](../../cpp/clrcall.md) (para código administrado). por **_beginthreadex**, es [__stdcall](../../cpp/stdcall.md) (para código nativo) o [__clrcall](../../cpp/clrcall.md) (para código administrado).

*stack_size*<br/>
Tamaño de la pila de un subproceso nuevo, o 0.

*arglist*<br/>
Lista de argumentos que se va a pasar a un nuevo subproceso, o **null**.

*Seguridad*<br/>
Puntero a una estructura de [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que determina si el identificador devuelto se puede heredar de procesos secundarios. Si la *seguridad* es **null**, el identificador no se puede heredar. Debe ser **null** para aplicaciones de Windows 95.

*initflag*<br/>
Marcas que controlan el estado inicial de un nuevo subproceso. Establezca *initflag* en 0 para que se ejecute inmediatamente, o en **CREATE_SUSPENDED** para crear el subproceso en un estado suspendido; Use [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) para ejecutar el subproceso. Establezca *initflag* en **STACK_SIZE_PARAM_IS_A_RESERVATION** marca para usar *STACK_SIZE* como tamaño de reserva inicial de la pila en bytes. Si no se especifica esta marca, *STACK_SIZE* especifica el tamaño de confirmación.

*thrdaddr*<br/>
Señala a una variable de 32 bits que recibe el identificador del subproceso. Si es **null**, no se utiliza.

## <a name="return-value"></a>Valor devuelto

Si es correcto, cada una de estas funciones devuelve un identificador al subproceso creado recientemente; sin embargo, si el subproceso recién creado sale demasiado rápido, es posible que **_beginthread** no devuelva un identificador válido. (Vea la explicación en la sección comentarios). En un error, **_beginthread** devuelve-1L y **errno** se establece en **EAGAIN** si hay demasiados subprocesos, en **EINVAL** si el argumento no es válido o el tamaño de la pila es incorrecto, o en **EACCES** si no hay suficientes recursos (por ejemplo, memoria). En un error, **_beginthreadex** devuelve 0 y se establecen **errno** y **_doserrno** .

Si *start_address* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven-1.

Para más información sobre estos y otros códigos devueltos, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener más información sobre **uintptr_t**, consulte [tipos estándar](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Observaciones

La función **_beginthread** crea un subproceso que comienza la ejecución de una rutina en *start_address*. La rutina en *start_address* debe usar la Convención de llamada **__cdecl** (para código nativo) o **__clrcall** (para código administrado) y no debe tener ningún valor devuelto. Cuando el subproceso vuelve de la rutina, finaliza automáticamente. Para obtener más información sobre los subprocesos, consulte [Compatibilidad del código antiguo con multithreading (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** es similar a la API [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) de Win32 más estrechamente que **_beginthread** . **_beginthreadex** difiere de **_beginthread** de las siguientes maneras:

- **_beginthreadex** tiene tres parámetros adicionales: *initflag*, *Security*y **threadaddr**. El nuevo subproceso se puede crear en un estado suspendido, con una seguridad especificada, y se puede tener acceso a él mediante *thrdaddr*, que es el identificador del subproceso.

- La rutina en *start_address* que se pasa a **_beginthreadex** debe utilizar la Convención de llamada **__stdcall** (para código nativo) o **__clrcall** (para código administrado) y debe devolver un código de salida del subproceso.

- **_beginthreadex** devuelve 0 en caso de error, en lugar de-1L.

- Un subproceso que se crea mediante **_beginthreadex** finaliza con una llamada a [_endthreadex](endthread-endthreadex.md).

La función **_beginthreadex** proporciona más control sobre cómo se crea el subproceso que **_beginthread** . La función **_endthreadex** también es más flexible. Por ejemplo, con **_beginthreadex**, puede usar la información de seguridad, establecer el estado inicial del subproceso (en ejecución o suspendido) y obtener el identificador del subproceso del subproceso recién creado. También puede usar el identificador de subproceso devuelto por **_beginthreadex** con las API de sincronización, lo que no se puede hacer con **_beginthread**.

Es más seguro usar **_beginthreadex** que **_beginthread**. Si el subproceso generado por **_beginthread** sale rápidamente, el identificador que se devuelve al autor de la llamada de **_beginthread** podría no ser válido o señalar a otro subproceso. Sin embargo, el identificador devuelto por **_beginthreadex** debe cerrarse por el autor de la llamada de **_beginthreadex**, por lo que se garantiza que sea un identificador válido si **_beginthreadex** no devolvió un error.

Puede llamar a [_endthread](endthread-endthreadex.md) o **_endthreadex** explícitamente para terminar un subproceso; sin embargo, **_endthread** o **_endthreadex** se llama automáticamente cuando el subproceso vuelve de la rutina que se pasa como parámetro. La finalización de un subproceso con una llamada a **_endthread** o **_endthreadex** ayuda a garantizar la recuperación correcta de los recursos que se asignan para el subproceso.

**_endthread** cierra automáticamente el identificador del subproceso, mientras que **_endthreadex** no lo hace. Por lo tanto, cuando utilice **_beginthread** y **_endthread**, no cierre explícitamente el identificador del subproceso llamando a la API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) de Win32. Este comportamiento difiere de la API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) de Win32.

> [!NOTE]
> En el caso de un archivo ejecutable vinculado con libcmt. lib, no llame a la API **ExitThread** de Win32 para no evitar que el sistema en tiempo de ejecución recupere los recursos asignados. **_endthread** y **_endthreadex** reclaman recursos de subprocesos asignados y después llaman a **ExitThread**.

El sistema operativo controla la asignación de la pila cuando se llama a **_beginthread** o **_beginthreadex** ; no tiene que pasar la dirección de la pila de subprocesos a cualquiera de estas funciones. Además, el argumento *STACK_SIZE* puede ser 0, en cuyo caso el sistema operativo utiliza el mismo valor que la pila que se especifica para el subproceso principal.

*arglist* es un parámetro que se va a pasar al subproceso recién creado. Normalmente, es la dirección de un elemento de datos, como una cadena de caracteres. *arglist* puede ser **null** si no es necesario, pero **_beginthread** y **_beginthreadex** deben tener algún valor para pasar al nuevo subproceso. Todos los subprocesos se terminan si cualquier subproceso llama a [Abort](abort.md), **Exit**, **_exit**o **ExitProcess**.

La configuración regional del nuevo subproceso se inicializa con la información de configuración regional actual de cada proceso. Si la configuración regional para cada subproceso está habilitada por una llamada a [_configthreadlocale](configthreadlocale.md) (ya sea globalmente o solo para nuevos subprocesos), el subproceso puede cambiar su configuración regional independientemente de otros subprocesos llamando a **setlocale** o **_wsetlocale**. Los subprocesos que no tienen establecida la marca de configuración regional por subproceso pueden afectar a la información de configuración regional de todos los demás subprocesos que tampoco tienen establecida la marca de configuración regional por subproceso, así como todos los subprocesos recién creados. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En el caso del código **/CLR** , **_beginthread** y **_beginthreadex** tienen dos sobrecargas. Uno toma un puntero de función de Convención de llamada nativo y el otro toma un puntero de función **__clrcall** . La primera sobrecarga no es una aplicación de dominio seguro y nunca lo será. Si está escribiendo código **/CLR** , debe asegurarse de que el nuevo subproceso entra en el dominio de aplicación correcto antes de tener acceso a los recursos administrados. Para ello, por ejemplo, use [call_in_appdomain (Función)](../../dotnet/call-in-appdomain-function.md). La segunda sobrecarga es segura para el dominio de aplicación; el subproceso recién creado finalizará siempre en el dominio de aplicación del llamador de **_beginthread** o **_beginthreadex**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo las versiones de multiproceso de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md) .

Para usar **_beginthread** o **_beginthreadex**, la aplicación debe vincularse a una de las bibliotecas en tiempo de ejecución multiproceso de C.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa **_beginthread** y **_endthread**.

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

// Bounce - Thread to create and control a colored letter that moves
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

En el código de ejemplo siguiente se muestra cómo puede usar el identificador de subproceso devuelto por **_beginthreadex** con la API de sincronización [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject). El subproceso principal espera que el segundo subproceso finalice antes de continuar. Cuando el segundo subproceso llama a **_endthreadex**, hace que su objeto de subproceso vaya al estado señalado. Esto permite que el subproceso principal continúe ejecutándose. Esto no se puede hacer con **_beginthread** y **_endthread**, porque **_endthread** llama a **CloseHandle**, que destruye el objeto de subproceso antes de que se pueda establecer en el estado señalado.

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

## <a name="see-also"></a>Consulta también

- [Control de proceso y entorno](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [aborta](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
