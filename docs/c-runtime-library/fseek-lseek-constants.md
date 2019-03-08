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
ms.openlocfilehash: a97495aaa5ab0a79ed71a48a12162bd14fc60131
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220457"
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
