---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537805"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Específicos de Microsoft**

Extrae y devuelve el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Comentarios

Extrae y devuelve el puntero de interfaz encapsulado y, a continuación, borra el almacenamiento del puntero encapsulado en NULL. Esto quita el puntero de interfaz de la encapsulación. Es decisión suya llamar a `Release` en el puntero de interfaz devuelto.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)