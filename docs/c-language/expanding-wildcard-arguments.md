---
title: Expandir argumentos de caracteres comodín
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: 2224d01eeb3ec54a9c0ff895dfa45574135f7c0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443425"
---
# <a name="expanding-wildcard-arguments"></a>Expandir argumentos de caracteres comodín

**Específicos de Microsoft**

Cuando se ejecuta un programa de C, se puede usar cualquiera de estos dos caracteres comodín —el signo de interrogación (?) y el asterisco (*)— para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.

De forma predeterminada, los caracteres comodín no se expanden en argumentos de línea de comandos. Puede reemplazar la rutina de carga `argv` del vector de argumento normal por una versión que expanda los caracteres comodín mediante la vinculación con el archivo setargv.obj o wsetargv.obj. Si el programa usa una función `main` , debe vincularse con setargv.obj. Si el programa usa una función `wmain` , debe vincularse con wsetargv.obj. Ambos tienen un comportamiento equivalente.

Para establecer la vinculación con setargv.obj o wsetargv.obj, use la opción **/link** . Por ejemplo:

**cl example.c /link setargv.obj**

Los caracteres comodín se expanden de la misma manera que los comandos del sistema operativo. (Vea la guía del usuario del sistema operativo si no está familiarizado con los caracteres comodín).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Opciones de vínculo](../c-runtime-library/link-options.md)<br/>
[Función main y ejecución del programa](../c-language/main-function-and-program-execution.md)