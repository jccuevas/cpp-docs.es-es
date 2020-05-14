---
title: Utilizar la versión de depuración para comprobar si se ha sobrescrito la memoria
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314291"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Utilizar la versión de depuración para comprobar si se ha sobrescrito la memoria

Para usar la compilación de depuración para comprobar si se ha sobrescrito la memoria, primero debe recompilar el proyecto para su depuración. A continuación, vaya al principio de la función `InitInstance` de la aplicación y agregue la siguiente línea:

```
afxMemDF |= checkAlwaysMemDF;
```

El asignador de memoria de depuración coloca bytes de protección en torno a todas las asignaciones de memoria. Estos bytes de protección no hacen nada, pero puede comprobar si se han cambiado, lo que indicaría una sobrescritura de memoria. De lo contrario, esto solo proporciona un búfer que, de hecho, le permite realizar una sobrescritura de memoria.

Al activar `checkAlwaysMemDF`, obliga a MFC a llamar a la función `AfxCheckMemory` cada vez que se realiza una llamada a **new** o **delete**. Si se detecta una sobrescritura de memoria, se generará un mensaje de seguimiento similar al siguiente:

```
Damage Occurred! Block=0x5533
```

Si ve uno de estos mensajes, debe examinar el código para determinar dónde se ha producido el daño. Para aislar más exactamente el punto en el que se ha producido la sobrescritura de memoria, puede realizar llamadas explícitas a `AfxCheckMemory` usted mismo. Por ejemplo:

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Si la primera llamada ASSERT se realiza correctamente y se produce un error en la segunda, significa que la sobrescritura de memoria se debe haber producido en la función entre las dos llamadas.

En función de la naturaleza de la aplicación, puede encontrarse con que `afxMemDF` hace que el programa se ejecute demasiado despacio como para hacer pruebas. La variable `afxMemDF` hace que se llame a `AfxCheckMemory` para cada llamada a "new" y "delete". En ese caso, debe dispersar sus propias llamadas a `AfxCheckMemory`() tal y como se ha mostrado anteriormente, e intentar aislar la sobrescritura de memoria de este modo.

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
