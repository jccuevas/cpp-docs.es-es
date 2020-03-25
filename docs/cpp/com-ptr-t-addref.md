---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 51182b461aeac83c12bb18a573a49b2d4347a190
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189938"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Específicos de Microsoft**

Llama a la función miembro `AddRef` de `IUnknown` en el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
void AddRef( );
```

## <a name="remarks"></a>Observaciones

Llama a `IUnknown::AddRef` en el puntero de interfaz encapsulado, lo que genera un error de `E_POINTER` si el puntero es NULL.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
