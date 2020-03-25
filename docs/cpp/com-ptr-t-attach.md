---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 870e3580ed23ce994d832f7c59b951680d725e41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180503"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Específicos de Microsoft**

Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.

## <a name="syntax"></a>Sintaxis

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parámetros

*pInterface*<br/>
Puntero a interfaz sin formato.

*fAddRef*<br/>
Si es TRUE, se llama a `AddRef`. Si es FALSE, el objeto de `_com_ptr_t` toma la propiedad del puntero de interfaz sin formato sin llamar a `AddRef`.

## <a name="remarks"></a>Observaciones

- No se llama a `AddRef` **Attach (** *pInterface* **)** . La propiedad de la interfaz se pasa a este objeto `_com_ptr_t`. se llama a `Release` para reducir el recuento de referencias del puntero encapsulado previamente.

- **Adjuntar (**  *pInterface* **,**  *fAddRef*  **)** Si *fAddRef* es true, se llama a `AddRef` para incrementar el recuento de referencias para el puntero de interfaz encapsulado. Si *fAddRef* es false, este objeto `_com_ptr_t` toma la propiedad del puntero de interfaz sin formato sin llamar a `AddRef`. se llama a `Release` para reducir el recuento de referencias del puntero encapsulado previamente.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
