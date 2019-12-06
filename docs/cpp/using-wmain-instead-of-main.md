---
title: Usar wmain en vez de main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: f47d7219a54b197ec59f109cf08879774b48e6f7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857221"
---
# <a name="using-wmain-instead-of-main"></a>Usar wmain en vez de main

**Específicos de Microsoft**

En el modelo de programación Unicode, puede definir una versión con caracteres anchos de la función `main`. Utilice **wmain** en lugar de `main` si desea escribir código portable que se adhiera a la especificación Unicode.

Declare los parámetros formales a **wmain** con un formato similar al `main`. A continuación, se pueden pasar al programa argumentos de caracteres anchos y, opcionalmente, un puntero a entorno de caracteres anchos. Los parámetros *argv* y *envp* de **wmain** son del tipo `wchar_t*`.

Si el programa utiliza una función de `main`, el entorno de caracteres multibyte lo crea el sistema operativo al inicio del programa. Solo se crea una copia de caracteres anchos del entorno cuando sea necesario (por ejemplo, mediante una llamada a las funciones [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) o [_wputenv](../c-runtime-library/reference/putenv-wputenv.md) ). En la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv` si ya existe un entorno MBCS, se crea un entorno correspondiente de cadena de caracteres anchos, y la variable global `_wenviron`, que es una versión con caracteres anchos de la variable global `_environ`, señala a dicho entorno. En este punto, existen dos copias del entorno (MBCS y Unicode) simultáneamente que el sistema operativo mantiene a lo largo de la vida del programa.

Del mismo modo, si el programa utiliza una función **wmain** , se crea un entorno MBCS (ASCII) en la primera llamada a `_putenv` o `getenv`, y la variable global `_environ` apunta a él.

Para obtener más información sobre el entorno MBCS, vea [conjuntos de caracteres de un solo byte y multibyte](../c-runtime-library/single-byte-and-multibyte-character-sets.md) en la referencia de la *biblioteca en tiempo de ejecución.*

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[main: Inicio de programa](../cpp/main-program-startup.md)