---
title: Clase is_trivially_copyable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2e2792c93b477c6d6aac4350045a506eda206eb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
