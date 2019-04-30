---
title: Advertencia de la línea de comandos D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 3fd8d442dfabaf2f03d8b564c9fdfb1537f6ff28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214212"
---
# <a name="command-line-warning-d9026"></a>Advertencia de la línea de comandos D9026

las opciones se aplican a toda la línea de comandos

Se especificó una opción en un comando después de que se especificó un nombre de archivo. La opción se aplica al archivo que le precede.

Por ejemplo, en el comando

```
CL verdi.c /G5 puccini.c
```

el archivo VERDI.c se compilará con la opción/G5, el valor predeterminado de no/G4.

Este comportamiento es diferente de algunas versiones anteriores, que se aplican solo las opciones especificadas antes el nombre de archivo, lo que resulta en VERDI.c que se compiló con/G4 y PUCCINI.c que se está compilando mediante/G5.