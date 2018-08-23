---
title: Compatibilidad con el uso de wmain | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- wWinMain
dev_langs:
- C++
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b82c233d1f03ae4679a355b6782bb9e7dd9dad15
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604068"
---
# <a name="support-for-using-wmain"></a>Compatibilidad con el uso de wmain
Visual C++ admite la definición de un **wmain** función y pasar argumentos de caracteres anchos a una aplicación Unicode. Declarar parámetros formales para **wmain**, utilizando un formato similar a `main`. A continuación, se pueden pasar al programa argumentos de caracteres anchos y, opcionalmente, un puntero a entorno de caracteres anchos. Los parámetros `argv` y `envp` de **wmain** son del tipo `wchar_t*`. Por ejemplo:  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  Aplicaciones de Unicode de MFC utilizan `wWinMain` como punto de entrada. En este caso, `CWinApp::m_lpCmdLine` es una cadena Unicode. No olvide establecer `wWinMainCRTStartup` con el [/Entry](../build/reference/entry-entry-point-symbol.md) opción del vinculador.  
  
 Si el programa utiliza una `main` función, se crea el entorno de caracteres multibyte en la biblioteca de tiempo de ejecución al inicio del programa. Se crea una copia de caracteres anchos del entorno sólo si es necesario (por ejemplo, por una llamada a las funciones `_wgetenv` o `_wputenv`). En la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv` si ya existe un entorno MBCS, se crea un entorno de cadena de caracteres anchos correspondiente. El entorno, a continuación, apunta el `_wenviron` variable global, que es una versión con caracteres anchos de la `_environ` variable global. En este punto, dos copias del entorno (MBCS y Unicode) existen simultáneamente y se mantienen por el sistema de tiempo de ejecución durante la vida del programa.  
  
 De forma similar, si el programa utiliza una función **wmain**, se crea un entorno de caracteres anchos durante el inicio del programa y la variable global `_wenviron` apunta a dicho entorno. Se crea un entorno MBCS (ASCII) en la primera llamada a `_putenv` o `getenv` y apunta la `_environ` variable global.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con Unicode](../text/support-for-unicode.md)   
 [Resumen de la programación de Unicode](../text/unicode-programming-summary.md)   
 [WinMain (función)](http://msdn.microsoft.com/library/windows/desktop/ms633559)