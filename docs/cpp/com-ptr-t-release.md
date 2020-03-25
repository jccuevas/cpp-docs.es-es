---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: f455e855e782a939e79898ee46e445f65d25d37a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170597"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Específicos de Microsoft**

Llama a la función miembro **Release** de `IUnknown` en el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
void Release( );
```

## <a name="remarks"></a>Observaciones

Llama a `IUnknown::Release` en el puntero de interfaz encapsulado, lo que genera un error de `E_POINTER` si este puntero de interfaz es NULL.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
