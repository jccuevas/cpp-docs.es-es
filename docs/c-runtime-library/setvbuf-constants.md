---
title: setvbuf (Constantes)
ms.date: 11/04/2016
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
ms.openlocfilehash: 661cf64c71e06c222503388df198d47429566602
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523811"
---
# <a name="setvbuf-constants"></a>setvbuf (Constantes)

## <a name="syntax"></a>Sintaxis

```

#include <stdio.h>
```

## <a name="remarks"></a>Comentarios

Estas constantes representan el tipo de búfer para `setvbuf`.

Los posibles valores se indican mediante las constantes de manifiesto siguientes:

|Constante|Significado|
|--------------|-------------|
|`_IOFBF`|Almacenamiento en búfer completo: se usa el búfer especificado en la llamada a `setvbuf` y su tamaño se corresponde con el especificado en la llamada `setvbuf`. Si el puntero de búfer es **NULL**, se usa el búfer del tamaño especificado asignado automáticamente.|
|`_IOLBF`|Igual a `_IOFBF`.|
|`_IONBF`|No se usa ningún búfer, con independencia de los argumentos de la llamada a `setvbuf`.|

## <a name="see-also"></a>Vea también

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)