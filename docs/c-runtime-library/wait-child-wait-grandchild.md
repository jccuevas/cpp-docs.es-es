---
title: _WAIT_CHILD, _WAIT_GRANDCHILD
ms.date: 11/04/2016
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
ms.openlocfilehash: 714b4e79f1c229817a12908aad0d726f74023036
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524396"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD, _WAIT_GRANDCHILD

## <a name="syntax"></a>Sintaxis

```

#include <process.h>
```

## <a name="remarks"></a>Comentarios

La función `_cwait` se puede usar en cualquier proceso para esperar a cualquier otro proceso (si se conoce el identificador de proceso). El argumento de acción puede ser cualquiera de los siguientes valores:

|Constante|Significado|
|--------------|-------------|
|`_WAIT_CHILD`|El proceso que realiza la llamada espera hasta que finaliza el proceso nuevo especificado.|
|`_WAIT_GRANDCHILD`|El proceso que realiza la llamada espera hasta que el nuevo proceso especificado y todos los procesos creados por ese proceso nuevo finalizan.|

## <a name="see-also"></a>Vea también

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)