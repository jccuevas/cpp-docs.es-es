---
title: fseek, _lseek (Constantes)
ms.date: 11/04/2016
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
ms.openlocfilehash: 67599ced3ee775d9e6d702a9fb9e66e0580240e4
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519157"
---
# <a name="fseek-lseek-constants"></a>fseek, _lseek (Constantes)

## <a name="syntax"></a>Sintaxis

```

#include <stdio.h>
```

## <a name="remarks"></a>Comentarios

El argumento *origin* especifica la posición inicial y puede ser una de las siguientes constantes de manifiesto:

|Constante|Significado|
|--------------|-------------|
|`SEEK_END`|Final de archivo|
|`SEEK_CUR`|Posición actual del puntero de archivo|
|`SEEK_SET`|Principio de archivo|

## <a name="see-also"></a>Vea también

[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)