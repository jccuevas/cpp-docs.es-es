---
title: Calcular valores necesarios
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 75952bbcdf823aa675b35702841c81e511105ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272655"
---
# <a name="calculating-necessary-values"></a>Calcular valores necesarios

Dos tipos de información esenciales deben calcularse la rutina de aplicación auxiliar de retraso. Para ello, hay dos funciones inline en delayhlp.cpp para calcular esta información.

- La primera calcula el índice de la importación actual en las tres tablas diferentes (importación (IAT) de tabla de direcciones, tabla de direcciones de importación enlazadas (BIAT) y tabla de direcciones de importación sin enlazar (UIAT)).

- La segunda cuenta el número de importaciones de una IAT válida.

```cpp
// utility function for calculating the index of the current import
// for all the tables (INT, BIAT, UIAT, and IAT).
__inline unsigned
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {
    return pitdCur - pitdBase;
    }

// utility function for calculating the count of imports given the base
// of the IAT. NB: this only works on a valid IAT!
__inline unsigned
CountOfImports(PCImgThunkData pitdBase) {
    unsigned        cRet = 0;
    PCImgThunkData  pitd = pitdBase;
    while (pitd->u1.Function) {
        pitd++;
        cRet++;
        }
    return cRet;
    }
```

## <a name="see-also"></a>Vea también

[Descripción de la función auxiliar](understanding-the-helper-function.md)
