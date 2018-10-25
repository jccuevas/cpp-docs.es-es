---
title: Enumeraciones del espacio de nombres de simultaneidad (AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58d70b995642eaca3dbefd75383e6d6bf06f2c62
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082442"
---
# <a name="concurrency-namespace-enums-amp"></a>Enumeraciones del espacio de nombres de simultaneidad (AMP)

|||
|-|-|
|[access_type (enumeración)](#access_type)|[queuing_mode (enumeración)](#queuing_mode)|

##  <a name="access_type"></a>  access_type (enumeración)

Tipo de enumeración se utiliza para denotar los distintos tipos de acceso a datos.

```
enum access_type;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`access_type_auto`|Elija automáticamente el mejor `access_type` para el acelerador.|
|`access_type_none`|Dedicado. La asignación solo está disponible en el acelerador y no en la CPU.|
|`access_type_read`|Compartido. La asignación está disponible en el acelerador y es legible en la CPU.|
|`access_type_read_write`|Compartido. La asignación está disponible en el acelerador y es modificable en la CPU.|
|`access_type_write`|Compartido. La asignación está disponible en el acelerador y es legible y modificable en la CPU.|

##  <a name="queuing_mode"></a>  queuing_mode (enumeración)

Especifica los modos de la puesta en cola que se admiten en el acelerador.

```
enum queuing_mode;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`queuing_mode_immediate`|Por ejemplo, un modo de puesta en cola que especifica que los comandos [parallel_for_each (función) (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), se envían al dispositivo acelerador correspondiente en cuanto vuelven al llamador.|
|`queuing_mode_automatic`|Un modo de puesta en cola que especifica que los comandos se encolan en una cola de comando que corresponde a la [accelerator_view](accelerator-view-class.md) objeto. Los comandos se envían al dispositivo cuando [accelerator_view:: Flush](accelerator-view-class.md#flush) se llama.|

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
