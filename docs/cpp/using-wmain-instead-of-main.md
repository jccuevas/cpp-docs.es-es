---
title: Usar wmain en vez de main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: 8cdc986d1582d2b26f137e3147ce78bc83e9daca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677765"
---
# <a name="using-wmain-instead-of-main"></a>Usar wmain en vez de main

## <a name="microsoft-specific"></a>Específicos de Microsoft

En el modelo de programación Unicode, puede definir una versión con caracteres anchos de la `main` función. Use **wmain** en lugar de `main` si desea escribir código portable conforme con la especificación Unicode.

Declarar parámetros formales para **wmain** utilizando un formato similar a `main`. A continuación, se pueden pasar al programa argumentos de caracteres anchos y, opcionalmente, un puntero a entorno de caracteres anchos. El *argv* y *envp* parámetros **wmain** son del tipo `wchar_t*`.

Si el programa utiliza una `main` función, se crea el entorno de caracteres multibyte por el sistema operativo al iniciar el programa. Se crea una copia de caracteres anchos del entorno solo cuando sea necesario (por ejemplo, mediante una llamada a la [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) o [_wputenv](../c-runtime-library/reference/putenv-wputenv.md) funciones). En la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv` si ya existe un entorno MBCS, se crea un entorno correspondiente de cadena de caracteres anchos, y la variable global `_wenviron`, que es una versión con caracteres anchos de la variable global `_environ`, señala a dicho entorno. En este punto, existen dos copias del entorno (MBCS y Unicode) simultáneamente que el sistema operativo mantiene a lo largo de la vida del programa.

De forma similar, si el programa utiliza una **wmain** función, se crea un entorno MBCS (ASCII) en la primera llamada a `_putenv` o `getenv`y apunta a la `_environ` variable global.

Para obtener más información sobre el entorno MBCS, vea [un solo byte y juegos de caracteres Multibyte](../c-runtime-library/single-byte-and-multibyte-character-sets.md) en el *referencia de la biblioteca de tiempo de ejecución.*

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[main: Inicio de programa](../cpp/main-program-startup.md)