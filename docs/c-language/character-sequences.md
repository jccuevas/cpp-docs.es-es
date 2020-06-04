---
title: Secuencias de caracteres
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: 42fb6b61771feb3eaedfb4ce1e674003df91b263
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312692"
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
