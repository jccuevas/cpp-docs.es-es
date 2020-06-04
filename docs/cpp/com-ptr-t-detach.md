---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: 8ba42f19e3474cc4a3199771f761b021221f430e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190019"
---
# <a name="_com_ptr_tdetach"></a>_com_ptr_t::Detach

**Específicos de Microsoft**

Extrae y devuelve el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Observaciones

Extrae y devuelve el puntero de interfaz encapsulado y, a continuación, borra el almacenamiento del puntero encapsulado como NULL. Esto quita el puntero de interfaz de la encapsulación. Depende de usted llamar a `Release` en el puntero de interfaz devuelto.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
