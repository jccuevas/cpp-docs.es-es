---
title: Definiciones de tipo &lt;new&gt;
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 85c8d0c2974f734783e3d9c2ad1269f84d605dec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549128"
---
# <a name="ltnewgt-typedefs"></a>Definiciones de tipo &lt;new&gt;

| |
| - |
|[new_handler](#new_handler)|

## <a name="new_handler"></a> new_handler

El tipo que apunta a una función que se puede usar como un controlador nuevo.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Comentarios

Este tipo de función de controlador se llama mediante **operatornew** o `operator new[]` cuando no pueden satisfacer una solicitud de almacenamiento adicional.

### <a name="example"></a>Ejemplo

Vea [set_new_handler](../standard-library/new-functions.md#set_new_handler) para obtener un ejemplo que usa `new_handler` como un valor devuelto.

## <a name="see-also"></a>Vea también

[\<new>](../standard-library/new.md)<br/>
