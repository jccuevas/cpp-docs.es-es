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
ms.openlocfilehash: 8936789f4e3c9349e9d79616c8506c044dc79f70
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220405"
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
