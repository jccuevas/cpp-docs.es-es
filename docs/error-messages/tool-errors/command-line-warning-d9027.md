---
title: Advertencia de la línea de comandos D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: f89e7416efe7a0069ee2dae8df921933bbe76bcf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482607"
---
# <a name="command-line-warning-d9027"></a>Advertencia de la línea de comandos D9027

archivo de código fuente '\<filename >' omite

CL.exe omite el archivo de origen de entrada.

Esta advertencia puede deberse a un espacio entre la opción /Fo y un nombre de archivo de salida en una línea de comandos con la opción /c. Por ejemplo:

```
cl /c /Fo output.obj input.c
```

Dado que hay un espacio entre /Fo y `output.obj`, CL.exe toma `output.obj` como el nombre del archivo de entrada. Para corregir el problema, quite el espacio:

```
cl /c /Fooutput.obj input.c
```