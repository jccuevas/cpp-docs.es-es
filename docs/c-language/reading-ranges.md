---
title: Intervalos de lectura
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: b5c6a6baf43b8786fbd0301e4b89ea856d839606
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604125"
---
# <a name="reading-ranges"></a>Intervalos de lectura

**ANSI 4.9.6.2** La interpretación de un carácter de guion (-) que no sea el primero ni el último carácter de scanlist para la conversión % [ en la función `fscanf`.

La línea siguiente

```
fscanf( fileptr, "%[A-Z]", strptr);
```

lee cualquier número de caracteres del intervalo A - Z en la cadena a la que `strptr` señala.

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)