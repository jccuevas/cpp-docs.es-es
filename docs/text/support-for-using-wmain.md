---
title: Compatibilidad con el uso de wmain
ms.date: 11/04/2016
f1_keywords:
- wWinMain
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
ms.openlocfilehash: 4af389c00f6065df631f891dadcb0b2f350f984d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491199"
---
# <a name="support-for-using-wmain"></a>Compatibilidad con el uso de wmain

Visual C++ permite definir una función **wmain** y pasar argumentos de caracteres anchos a la aplicación Unicode. Los parámetros formales se declaran en **wmain**, con `main`un formato similar a. A continuación, se pueden pasar al programa argumentos de caracteres anchos y, opcionalmente, un puntero a entorno de caracteres anchos. Los parámetros `argv` y `envp` de **wmain** son del tipo `wchar_t*`. Por ejemplo:

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> Las aplicaciones Unicode MFC `wWinMain` utilizan como punto de entrada. En este caso, `CWinApp::m_lpCmdLine` es una cadena Unicode. Asegúrese de establecer `wWinMainCRTStartup` con la opción del enlazador [/entry](../build/reference/entry-entry-point-symbol.md) .

Si el programa utiliza una función **main**, el entorno de caracteres multibyte lo crea la biblioteca en tiempo de ejecución durante el inicio del programa. Se crea una copia de caracteres anchos del entorno sólo si es necesario (por ejemplo, por una llamada a las funciones `_wgetenv` o `_wputenv`). En la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv` si ya existe un entorno MBCS, se crea un entorno de cadena de caracteres anchos correspondiente. Después, el entorno se señala mediante la `_wenviron` variable global, que es una versión con caracteres anchos de `_environ` la variable global. En este momento, existen dos copias del entorno (MBCS y Unicode) simultáneamente y las mantiene el sistema en tiempo de ejecución a lo largo de la vida del programa.

De forma similar, si el programa utiliza una función **wmain**, se crea un entorno de caracteres anchos durante el inicio del programa y la variable global `_wenviron` apunta a dicho entorno. Se crea un entorno MBCS (ASCII) en la primera llamada a `_putenv` o `getenv` , y la variable global apunta `_environ` a él.

## <a name="see-also"></a>Vea también

[Compatibilidad con Unicode](../text/support-for-unicode.md)<br/>
[Resumen de la programación con Unicode](../text/unicode-programming-summary.md)<br/>
[WinMain (función)](/windows/win32/api/winbase/nf-winbase-winmain)
