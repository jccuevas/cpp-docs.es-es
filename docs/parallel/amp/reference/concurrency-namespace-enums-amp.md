---
title: Enumeraciones del espacio de nombres de simultaneidad (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: a4feb2f98fc288fa79c0f9d81e4ed882027eddf8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424978"
---
# <a name="concurrency-namespace-enums-amp"></a>Enumeraciones del espacio de nombres de simultaneidad (AMP)

|||
|-|-|
|[Enumeración access_type](#access_type)|[Enumeración queuing_mode](#queuing_mode)|

## <a name="access_type"></a>Enumeración access_type

Tipo de enumeración usado para denotar los distintos tipos de acceso a los datos.

```cpp
enum access_type;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`access_type_auto`|Elija automáticamente el mejor `access_type` para el acelerador.|
|`access_type_none`|Dedicó. La asignación solo es accesible en el acelerador y no en la CPU.|
|`access_type_read`|Recurso. La asignación es accesible en el acelerador y es legible en la CPU.|
|`access_type_read_write`|Recurso. La asignación es accesible en el acelerador y se puede escribir en la CPU.|
|`access_type_write`|Recurso. La asignación es accesible en el acelerador y es legible y grabable en la CPU.|

## <a name="queuing_mode"></a>Enumeración queuing_mode

Especifica los modos de la puesta en cola que se admiten en el acelerador.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`queuing_mode_immediate`|Un modo de puesta en cola que especifica que cualquier comando, por ejemplo [Parallel_for_eachC++ función (amp)](concurrency-namespace-functions-amp.md#parallel_for_each), se envía al dispositivo de acelerador correspondiente en cuanto vuelve al autor de la llamada.|
|`queuing_mode_automatic`|Modo de puesta en cola que especifica que los comandos se ponen en cola en una cola de comandos que corresponde al objeto de [accelerator_view](accelerator-view-class.md) . Los comandos se envían al dispositivo cuando se llama a [accelerator_view:: Flush](accelerator-view-class.md#flush) .|

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
