---
title: Advertencia de la línea de comandos D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 59dfcdc97fb9caf60a018cb20583ee6fca3dcb27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196708"
---
# <a name="command-line-warning-d9026"></a>Advertencia de la línea de comandos D9026

las opciones se aplican a toda la línea de comandos

Se especificó una opción en un comando después de especificar un nombre de archivo. La opción se aplicó al archivo que lo precedía.

Por ejemplo, en el comando

```
CL verdi.c /G5 puccini.c
```

el archivo VERDI. c se compilará con la opción/G5, no con el valor predeterminado de/G4.

Este comportamiento es diferente al de algunas versiones anteriores, que solo aplicaban las opciones especificadas antes del nombre de archivo, lo que da lugar a que VERDI. c se compilara con/G4 y PUCCINI. c compilando mediante/G5.
