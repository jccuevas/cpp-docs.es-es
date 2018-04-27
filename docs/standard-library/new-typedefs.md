---
title: Definiciones de tipo &lt;new&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: 7
manager: ghogen
ms.openlocfilehash: 53a13168986171d3240cc15e405fc08b3db07e96
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ltnewgt-typedefs"></a>Definiciones de tipo &lt;new&gt;

||
|-|
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
