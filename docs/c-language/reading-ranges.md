---
title: Intervalos de lectura
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: 86bb24647084d8bdc452960bab631587c2413276
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343148"
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
