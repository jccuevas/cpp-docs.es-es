---
title: Clase is_trivially_copyable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 177ba6e688f6d7ed2b4c76eb0ede95cc288b1d5d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857537"
---
# <a name="istriviallycopyable-class"></a>Clase is_trivially_copyable

Comprueba si el tipo se puede copiar de forma trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>Parámetros

`T` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `T` se puede copiar de forma trivial; en caso contrario, es false. Los tipos que se pueden copiar de forma trivial no tienen operaciones de copia, operaciones de movimiento ni destructores no triviales. Por lo general, una operación de copia se considera trivial si se puede implementar como una copia bit a bit. Tanto las matrices de tipos que se pueden copiar de forma trivial como los tipos integrados se pueden copiar de forma trivial.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
