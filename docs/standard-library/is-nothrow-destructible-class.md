---
title: Clase is_nothrow_destructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_destructible
helpviewer_keywords:
- is_nothrow_destructible
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
ms.openlocfilehash: 366b40af45c57d058d918c4c2f21d1b2ba486d35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656747"
---
# <a name="isnothrowdestructible-class"></a>Clase is_nothrow_destructible

Comprueba si el tipo se puede destruir y el compilador sabe que el destructor no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_nothrow_destructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es un tipo puede destruir y el destructor se sabe que el compilador no se inicia. En caso contrario, es False.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
