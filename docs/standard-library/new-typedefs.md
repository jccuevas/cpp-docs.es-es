---
title: Definiciones de tipo &lt;new&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 5ab0087a85cb2fce6fa300db136e7c60c66b0b5c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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
