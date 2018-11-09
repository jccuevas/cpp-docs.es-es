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
ms.openlocfilehash: fcf2c7ac6ea6280abdab5279ab67b65656bdeff9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507691"
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