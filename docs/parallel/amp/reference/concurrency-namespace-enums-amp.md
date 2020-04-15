---
title: Enumeraciones del espacio de nombres de simultaneidad (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: 2467db27ad36dfcda31dfb5bb45067ada5470d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376319"
---
# <a name="concurrency-namespace-enums-amp"></a>Enumeraciones del espacio de nombres de simultaneidad (AMP)

|||
|-|-|
|[access_type (Enumeración)](#access_type)|[queuing_mode (enumeración)](#queuing_mode)|

## <a name="access_type-enumeration"></a><a name="access_type"></a>access_type (enumeración)

Tipo de enumeración utilizado para denotar los distintos tipos de acceso a los datos.

```cpp
enum access_type;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`access_type_auto`|Elige automáticamente `access_type` lo mejor para el acelerador.|
|`access_type_none`|Dedicado. La asignación solo es accesible en el acelerador y no en la CPU.|
|`access_type_read`|Compartido. La asignación es accesible en el acelerador y es legible en la CPU.|
|`access_type_read_write`|Compartido. La asignación es accesible en el acelerador y se puede escribir en la CPU.|
|`access_type_write`|Compartido. La asignación es accesible en el acelerador y es legible y grabable en la CPU.|

## <a name="queuing_mode-enumeration"></a><a name="queuing_mode"></a>queuing_mode (enumeración)

Especifica los modos de la puesta en cola que se admiten en el acelerador.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`queuing_mode_immediate`|Un modo de cola que especifica que los comandos, por ejemplo, [parallel_for_each Function (C++ AMP),](concurrency-namespace-functions-amp.md#parallel_for_each)se envían al dispositivo acelerador correspondiente tan pronto como regresan al autor de la llamada.|
|`queuing_mode_automatic`|Un modo de cola que especifica que los comandos se pongan en cola en una cola de mandatos que corresponda al objeto [accelerator_view.](accelerator-view-class.md) Los comandos se envían al dispositivo cuando se llama [a accelerator_view::flush.](accelerator-view-class.md#flush)|

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
