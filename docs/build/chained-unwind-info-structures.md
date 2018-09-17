---
title: Encadenar las estructuras de información de desenredo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6da09387595188026d855fb99a49b588e6f21aa3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715031"
---
# <a name="chained-unwind-info-structures"></a>Estructuras encadenadas de información de desenredo

Si se establece la marca UNW_FLAG_CHAININFO, a continuación, una estructura de información de desenredo es un secundario y el campo de dirección de excepción-controlador/encadenadas-info compartido contiene la información de desenredo principal. El código siguiente recupera información, suponiendo que de desenredo de la réplica principal `unwindInfo` es la estructura que tiene el UNW_FLAG_CHAININFO marcador establecido.

```
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Información encadenada es útil en dos situaciones. En primer lugar, se puede usar para los segmentos de código no contiguos. Mediante el uso de información encadenada, puede reducir el tamaño de la información de desenredo necesaria, porque no tiene que duplicar la matriz de códigos de desenredado de la información de desenredo principal.

También puede usar información encadenada para agrupar registros volátiles. El compilador puede retrasar guardar algunos registros variables hasta que está fuera del prólogo de función de entrada. Puede registrar esto haciendo que la información de desenredo principal para la parte de la función delante del código agrupado y, a continuación, configurar información encadenada con un tamaño distinto de cero de prólogo, donde los códigos de desenredado de la información encadenada reflejan guardado los registros no volátiles. En ese caso, los códigos de desenredado son todas las instancias de UWOP_SAVE_NONVOL. No se admite una agrupación que guarda los registros no volátiles, mediante una INSERCIÓN o modifica el registro RSP mediante el uso de una asignación fija adicional de la pila.

Un elemento UNWIND_INFO con UNW_FLAG_CHAININFO establecido puede contener una entrada RUNTIME_FUNCTION cuyo elemento UNWIND_INFO también tenga UNW_FLAG_CHAININFO establecido (ajuste de reducción múltiple). Finalmente, la información de desenredo encadenada punteros llegará a un elemento UNWIND_INFO con UNW_FLAG_CHAININFO desactivada; Este es el elemento UNWIND_INFO principal, que señala al punto de entrada del procedimiento real.

## <a name="see-also"></a>Vea también

[Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)