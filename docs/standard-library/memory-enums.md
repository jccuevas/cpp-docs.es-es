---
title: Enumeraciones &lt;memory&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 9b9ea485bb66292c3c0509036c22dd161a694dd3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961427"
---
# <a name="ltmemorygt-enums"></a>Enumeraciones &lt;memory&gt;

||
|-|
|[pointer_safety](#pointer_safety)|

## <a name="pointer_safety"></a>  Enumeración pointer_safety

Enumeración de los posibles valores devueltos por `get_pointer_safety`.

class pointer_safety { relaxed, preferred, strict };

### <a name="remarks"></a>Comentarios

El ámbito **enum** define los valores que pueden devolver `get_pointer_safety()`:

`relaxed`: los punteros derivados de forma no segura (como punteros a objetos declarados o asignados) se tratan igual que los derivados de forma segura.

`preferred`: como antes, pero los punteros derivados de forma no segura no se deben desreferenciar.

`strict`: los punteros derivados de forma no segura se pueden tratar de manera diferente que los derivados de forma segura.

## <a name="see-also"></a>Vea también

[\<memory>](../standard-library/memory.md)<br/>
