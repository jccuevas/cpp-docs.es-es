---
title: Utilizar la versión de depuración para comprobar si se ha sobrescrito la memoria
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314291"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Utilizar la versión de depuración para comprobar si se ha sobrescrito la memoria

Para usar la compilación de depuración para comprobar si la sobrescritura de memoria, primero debe recompilar el proyecto para la depuración. A continuación, vaya hasta el principio de la aplicación `InitInstance` funcione y agregue la siguiente línea:

```
afxMemDF |= checkAlwaysMemDF;
```

El asignador de memoria de depuración coloca bytes de protección para todas las asignaciones de memoria. Sin embargo, estos bytes de protección no hace nada bueno, a menos que compruebe si se han cambiado (lo que indicaría una sobrescritura de memoria). En caso contrario, esto simplemente proporciona un búfer que es posible que, de hecho, podrá superar una sobrescritura de memoria.

Activando el `checkAlwaysMemDF`, se forzará MFC para realizar una llamada a la `AfxCheckMemory` función cada vez que una llamada a **nueva** o **eliminar** se realiza. Si se ha detectado una sobrescritura de memoria, generará un mensaje de seguimiento que tiene un aspecto similar al siguiente:

```
Damage Occurred! Block=0x5533
```

Si ve uno de estos mensajes, deberá recorrer el código para determinar dónde se produjo el daño. Para aislar más exactamente donde se produjo la sobrescritura de memoria, puede realizar llamadas explícitas a `AfxCheckMemory` usted mismo. Por ejemplo:

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Si la primera comprobación se realiza correctamente y el segundo se produce un error, significa que debe haberse producido la sobrescritura de memoria en la función entre las dos llamadas.

Según la naturaleza de la aplicación, es posible que `afxMemDF` hace que el programa se ejecute muy lentamente, incluso para pruebas. El `afxMemDF` hace que la variable `AfxCheckMemory` llamará para cada llamada a new y delete. En ese caso, debería separar sus propias llamadas para `AfxCheckMemory`() como se indicó anteriormente e intente aislar la memoria sobrescriben de ese modo.

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
