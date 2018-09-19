---
title: Intervalos de lectura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76530dfdac917dfbde50bc3fb1b17a3c31178729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030251"
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