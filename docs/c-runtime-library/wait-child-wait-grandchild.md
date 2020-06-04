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
ms.openlocfilehash: 98858058add6a0a11d4f9331989c6816e38130aa
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745053"
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
