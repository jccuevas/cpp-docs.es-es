---
title: Ejemplo de programa multiproceso en C
ms.date: 08/09/2019
ms.assetid: 4706f6cd-ff9c-4dbf-99a2-1c999b568f17
ms.openlocfilehash: eb1a07558dd9446e167c27ad08891f88c37fb4ec
ms.sourcegitcommit: b3d19b5f59f3a5d90c24f9f16c73bad4c5eb6944
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195818"
---
# <a name="sample-multithread-c-program"></a>Ejemplo de programa multiproceso en C

Bounce. c es un programa multiproceso de ejemplo que crea un nuevo subproceso cada vez `a` que `A` se escribe la letra o. Cada subproceso rebota una letra de un color diferente alrededor de la pantalla. Se pueden crear hasta 32 subprocesos. La terminación normal del programa se produce `q` cuando `Q` se escribe o.

## <a name="compile-and-link-a-multithread-program"></a>Compilar y vincular un programa multiproceso

Los programas se compilan como multiproceso de forma predeterminada.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Para compilar y vincular el programa multiproceso. c desde el entorno de desarrollo

::: moniker range=">=vs-2019"

1. En el menú **Archivo**, elija **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **crear un nuevo proyecto** , seleccione la plantilla **aplicación** de **C++** consola que tiene, **Windows**y etiquetas de **consola** . Elija **Siguiente** para continuar.

1. En el cuadro de diálogo **configurar el nuevo proyecto** , escriba un nombre para el proyecto, como "rebote". Elija **crear** para continuar.

1. En la ventana de **Explorador de soluciones** , abra la carpeta **archivos de código fuente** en el proyecto y cambie el nombre del archivo de origen para que tenga la extensión. c.

1. En la ventana de edición, elimine el código fuente existente y reemplácelo por el código de ejemplo.

1. En el menú **Compilar** , elija **Compilar solución**.

1. Presione **F5** para iniciar el programa en el depurador.

::: moniker-end

::: moniker range="<=vs-2017"

1. En el menú **Archivo**, elija **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **nuevo proyecto** , seleccione  **C++ visual** en el panel izquierdo y, a continuación, seleccione **proyecto vacío** en el panel central.

1. En el cuadro de edición **nombre** , escriba un nombre para el proyecto, como "rebote". Elija **Aceptar** para crear el proyecto vacío.

1. En la ventana de **Explorador de soluciones** , abra la carpeta **archivos de código fuente** en el proyecto y agregue el archivo que contiene el código fuente de C al proyecto.

1. En el menú **compilar** , compile el proyecto; para ello, elija el comando **compilar solución** .

1. Presione **F5** para iniciar el programa en el depurador.

::: moniker-end

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Para compilar y vincular el programa multiproceso. c desde la línea de comandos

1. Compile y vincule el programa:

    ```cmd
    cl bounce.c
    ```

## <a name="example"></a>Ejemplo

Para compilar en la línea de comandos, copie y guarde este ejemplo en un archivo de código fuente con la extensión. c. En el IDE, Reemplace cualquier código fuente creado por la plantilla con este ejemplo:

```C
// sample_multithread_c_program.c
// compile with: /c
//
//  Bounce - Creates a new thread each time the letter 'a' is typed.
//  Each thread bounces a character of a different color around
//  the screen. All threads are terminated when the letter 'Q' is
//  entered.
//

#include <windows.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <conio.h>
#include <process.h>

#define MAX_THREADS  32

// The function getrandom returns a random number between
// min and max, which must be in integer range.
#define getrandom( min, max ) (SHORT)((rand() % (int)(((max) + 1) - \
                               (min))) + (min))

int main(void);                    // Thread 1: main
void KbdFunc(void);                // Keyboard input, thread dispatch
void BounceProc(void* MyID);       // Threads 2 to n: display
void ClearScreen(void);            // Screen clear
void ShutDown(void);               // Program shutdown
void WriteTitle(int ThreadNum);    // Display title bar information

HANDLE  hConsoleOut;                 // Handle to the console
HANDLE  hRunMutex;                   // "Keep Running" mutex
HANDLE  hScreenMutex;                // "Screen update" mutex
int     ThreadNr;                    // Number of threads started
CONSOLE_SCREEN_BUFFER_INFO csbiInfo; // Console information
COORD   consoleSize;
BOOL    bTrails;

int main() // Thread One
{
    // Get display screen information & clear the screen.
    hConsoleOut = GetStdHandle(STD_OUTPUT_HANDLE);
    GetConsoleScreenBufferInfo(hConsoleOut, &csbiInfo);
    consoleSize.X = csbiInfo.srWindow.Right;
    consoleSize.Y = csbiInfo.srWindow.Bottom;
    ClearScreen();
    WriteTitle(0);

    // Create the mutexes and reset thread count.
    hScreenMutex = CreateMutexW(NULL, FALSE, NULL);  // Cleared
    hRunMutex = CreateMutexW(NULL, TRUE, NULL);      // Set
    ThreadNr = 0;
    bTrails = FALSE;

    // Start waiting for keyboard input to dispatch threads or exit.
    KbdFunc();

    // All threads done. Clean up handles.
    if (hScreenMutex) CloseHandle(hScreenMutex);
    if (hRunMutex) CloseHandle(hRunMutex);
    if (hConsoleOut) CloseHandle(hConsoleOut);
}

void ShutDown(void) // Shut down threads
{
    while (ThreadNr > 0)
    {
        // Tell thread to die and record its death.
        ReleaseMutex(hRunMutex);
        ThreadNr--;
    }

    // Clean up display when done
    WaitForSingleObject(hScreenMutex, INFINITE);
    ClearScreen();
}

void KbdFunc(void) // Dispatch and count threads.
{
    int         KeyInfo;

    do
    {
        KeyInfo = _getch();
        if (tolower(KeyInfo) == 'a' &&
            ThreadNr < MAX_THREADS)
        {
            ThreadNr++;
            _beginthread(BounceProc, 0, &ThreadNr);
            WriteTitle(ThreadNr);
        }
        if (tolower(KeyInfo) == 't')
        {
            bTrails = !bTrails;
        }
    } while (tolower(KeyInfo) != 'q');

    ShutDown();
}

void BounceProc(void* pMyID)
{
    wchar_t MyCell, OldCell;
    WORD    MyAttrib, OldAttrib = 0;
    wchar_t BlankCell = 0x20;
    COORD   Coords, Delta;
    COORD   Old = { 0,0 };
    DWORD   Dummy;
    char* MyID = (char*)pMyID;

    // Generate update increments and initial
    // display coordinates.
    srand((unsigned int)* MyID * 3);

    Coords.X = getrandom(0, consoleSize.X - 1);
    Coords.Y = getrandom(0, consoleSize.Y - 1);
    Delta.X = getrandom(-3, 3);
    Delta.Y = getrandom(-3, 3);

    // Set up character & generate color
    // attribute from thread number.
    if (*MyID > 16)
        MyCell = 0x60 + *MyID - 16; // lower case
    else
        MyCell = 0x40 + *MyID;      // upper case
    MyAttrib = *MyID & 0x0f;   // force black background

    do
    {
        // Wait for display to be available, then lock it.
        WaitForSingleObject(hScreenMutex, INFINITE);

        if (!bTrails)
        {
            // If we still occupy the old screen position, blank it out.
            ReadConsoleOutputCharacterW(hConsoleOut, &OldCell, 1,
                Old, &Dummy);
            ReadConsoleOutputAttribute(hConsoleOut, &OldAttrib, 1,
                Old, &Dummy);
            if ((OldCell == MyCell) && (OldAttrib == MyAttrib))
                WriteConsoleOutputCharacterW(hConsoleOut, &BlankCell, 1,
                    Old, &Dummy);
        }

        // Draw new character, then clear screen lock
        WriteConsoleOutputCharacterW(hConsoleOut, &MyCell, 1,
            Coords, &Dummy);
        WriteConsoleOutputAttribute(hConsoleOut, &MyAttrib, 1,
            Coords, &Dummy);
        ReleaseMutex(hScreenMutex);

        // Increment the coordinates for next placement of the block.
        Old.X = Coords.X;
        Old.Y = Coords.Y;
        Coords.X += Delta.X;
        Coords.Y += Delta.Y;

        // If we are about to go off the screen, reverse direction
        if (Coords.X < 0 || Coords.X >= consoleSize.X)
        {
            Delta.X = -Delta.X;
            Beep(400, 50);
        }
        if (Coords.Y < 0 || Coords.Y > consoleSize.Y)
        {
            Delta.Y = -Delta.Y;
            Beep(600, 50);
        }
    }
    // Repeat while RunMutex is still taken.
    while (WaitForSingleObject(hRunMutex, 75L) == WAIT_TIMEOUT);
}

void WriteTitle(int ThreadNum)
{
    enum
    {
        sizeOfNThreadMsg = 120
    };
    wchar_t    NThreadMsg[sizeOfNThreadMsg] = { L"" };

    swprintf_s(NThreadMsg, sizeOfNThreadMsg,
        L"Threads running: %02d.  Press 'A' "
        L"to start a thread, 'T' to toggle "
        L"trails, 'Q' to quit.", ThreadNum);
    SetConsoleTitleW(NThreadMsg);
}

void ClearScreen(void)
{
    DWORD    dummy = 0;
    COORD    Home = { 0, 0 };
    FillConsoleOutputCharacterW(hConsoleOut, L' ',
        consoleSize.X * consoleSize.Y,
        Home, &dummy);
}
```

## <a name="see-also"></a>Vea también

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)
