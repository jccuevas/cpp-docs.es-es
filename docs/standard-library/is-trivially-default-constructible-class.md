---
title: Clase is_trivially_default_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa7b831790804005f0649dbae0dbb98df5121106
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954739"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible (clase)

Comprueba si el tipo tiene un constructor predeterminado trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un constructor trivial; en caso contrario, es false.

Un constructor predeterminado para una clase *Ty* es trivial si:

- es un constructor predeterminado declarado implícitamente

- la clase *Ty* no tiene ninguna función virtual

- la clase *Ty* tiene ninguna base virtual

- todas las bases directas de la clase *Ty* tienen constructores triviales

- las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores triviales

- las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores triviales

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
