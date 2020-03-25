---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 26dda2dff83ff0adbb7ef05c5e75f64b44138bd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170676"
---
# <a name="_com_ptr_tqueryinterface"></a>_com_ptr_t::QueryInterface

**Específicos de Microsoft**

Llama a la función miembro **QueryInterface** de `IUnknown` en el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>Parámetros

*suscripto*<br/>
`IID` de un puntero de interfaz.

*p*<br/>
Puntero de interfaz sin formato.

## <a name="remarks"></a>Observaciones

Llama a `IUnknown::QueryInterface` en el puntero de interfaz encapsulado con el `IID` especificado y devuelve el puntero de interfaz sin formato resultante en *p*. Esta rutina devuelve HRESULT para indicar si se ha realizado correctamente o no.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
