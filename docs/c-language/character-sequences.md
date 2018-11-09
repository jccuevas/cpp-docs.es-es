---
title: Secuencias de caracteres
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: dea24a2ae5887ea8c0111d8251ba4d9d03ccba0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489666"
---
# <a name="character-sequences"></a>Secuencias de caracteres

**ANSI 3.8.2** Asignación de secuencias de caracteres del archivo de código fuente

Las instrucciones de preprocesador utilizan el mismo juego de caracteres que las instrucciones del archivo de código fuente, con la excepción de que no se admiten secuencias de escape.

Así, para especificar una ruta de acceso para un archivo de inclusión, se usa una sola barra diagonal inversa:

```
#include "path1\path2\myfile"
```

En el código fuente, se requieren dos barras diagonales inversas:

```
fil = fopen( "path1\\path2\\myfile", "rt" );
```

## <a name="see-also"></a>Vea también

[Preprocesar directivas](../c-language/preprocessing-directives.md)