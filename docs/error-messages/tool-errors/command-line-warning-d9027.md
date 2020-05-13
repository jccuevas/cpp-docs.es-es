---
title: Advertencia de la línea de comandos D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 46ed5750bd1f315f20658ace9b83fac532fbbabb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196683"
---
# <a name="command-line-warning-d9027"></a>Advertencia de la línea de comandos D9027

se ha omitido el archivo de código fuente '\<filename > '

CL. exe omitió el archivo de origen de entrada.

Esta advertencia puede deberse a un espacio entre la opción/FO y un nombre de archivo de salida en una línea de comandos con la opción/c. Por ejemplo:

```
cl /c /Fo output.obj input.c
```

Dado que hay un espacio entre/FO y `output.obj`, CL. exe toma `output.obj` como el nombre del archivo de entrada. Para solucionar el problema, quite el espacio:

```
cl /c /Fooutput.obj input.c
```
