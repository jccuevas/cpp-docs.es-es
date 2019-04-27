---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154973"
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