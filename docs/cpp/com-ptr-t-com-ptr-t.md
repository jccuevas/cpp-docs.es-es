---
title: _com_ptr_t::_com_ptr_t
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::_com_ptr_t
helpviewer_keywords:
- _com_ptr_t method [C++]
ms.assetid: 0c00620a-28d2-4f60-ae4a-1696be36137e
ms.openlocfilehash: 779fd1008f6763f4b5ca95938018a5129e89aa1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154882"
---
# <a name="comptrtcomptrt"></a>_com_ptr_t::_com_ptr_t

**Específicos de Microsoft**

Construye un **_com_ptr_t** objeto.

## <a name="syntax"></a>Sintaxis

```
// Default constructor.
// Constructs a NULL smart pointer.
_com_ptr_t() throw();

// Constructs a NULL smart pointer. The NULL argument must be zero.
_com_ptr_t(
   int null
);

// Constructs a smart pointer as a copy of another instance of the
// same smart pointer. AddRef is called to increment the reference
// count for the encapsulated interface pointer.
_com_ptr_t(
   const _com_ptr_t& cp
) throw();

// Move constructor (Visual Studio 2015 Update 3 and later)
_com_ptr_t(_com_ptr_t&& cp) throw();

// Constructs a smart pointer from a raw interface pointer of this
// smart pointer's type. If fAddRef is true, AddRef is called
// to increment the reference count for the encapsulated
// interface pointer. If fAddRef is false, this constructor
// takes ownership of the raw interface pointer without calling AddRef.
_com_ptr_t(
   Interface* pInterface,
   bool fAddRef
) throw();

// Construct pointer for a _variant_t object.
// Constructs a smart pointer from a _variant_t object. The
// encapsulated VARIANT must be of type VT_DISPATCH or VT_UNKNOWN, or
// it can be converted into one of these two types. If QueryInterface
// fails with an E_NOINTERFACE error, a NULL smart pointer is
// constructed.
_com_ptr_t(
   const _variant_t& varSrc
);

// Constructs a smart pointer given the CLSID of a coclass. This
// function calls CoCreateInstance, by the member function
//  CreateInstance, to create a new COM object and then queries for
// this smart pointer's interface type. If QueryInterface fails with
// an E_NOINTERFACE error, a NULL smart pointer is constructed.
explicit _com_ptr_t(
   const CLSID& clsid, 
   IUnknown* pOuter = NULL, 
   DWORD dwClsContext = CLSCTX_ALL
);

// Calls CoCreateClass with provided CLSID retrieved from string.
explicit _com_ptr_t(
   LPCWSTR str, 
   IUnknown* pOuter = NULL, 
   DWORD dwClsContext = CLSCTX_ALL
);

// Constructs a smart pointer given a multibyte character string that
// holds either a CLSID (starting with "{") or a ProgID. This function
// calls CoCreateInstance, by the member function CreateInstance, to
// create a new COM object and then queries for this smart pointer's
// interface type. If QueryInterface fails with an E_NOINTERFACE error,
// a NULL smart pointer is constructed.
explicit _com_ptr_t(
   LPCSTR str,
   IUnknown* pOuter = NULL,
   DWORD dwClsContext = CLSCTX_ALL
);

// Saves the interface.
template<> 
_com_ptr_t(
   Interface* pInterface
) throw();

// Make sure correct ctor is called
template<> 
_com_ptr_t(
   LPSTR str
);

// Make sure correct ctor is called
template<> 
_com_ptr_t(
   LPWSTR str
);

// Constructs a smart pointer from a different smart pointer type or
// from a different raw interface pointer. QueryInterface is called to
// find an interface pointer of this smart pointer's type. If
// QueryInterface fails with an E_NOINTERFACE error, a NULL smart
// pointer is constructed.
template<typename _OtherIID> 
_com_ptr_t(
   const _com_ptr_t<_OtherIID>& p
);

// Constructs a smart-pointer from any IUnknown-based interface pointer.
template<typename _InterfaceType>
_com_ptr_t(
   _InterfaceType* p
);

// Disable conversion using _com_ptr_t* specialization of
// template<typename _InterfaceType> _com_ptr_t(_InterfaceType* p)
template<> 
explicit _com_ptr_t(
   _com_ptr_t* p
);
```

#### <a name="parameters"></a>Parámetros

*pInterface*<br/>
Puntero a interfaz sin formato.

*fAddRef*<br/>
Si es TRUE, `AddRef` se llama para incrementar el recuento de referencias del puntero de interfaz encapsulado.

*cp*<br/>
Un **_com_ptr_t** objeto.

*p*<br/>
Un puntero de interfaz sin formato, cuyo tipo es diferente del tipo de puntero inteligente de este **_com_ptr_t** objeto.

*varSrc*<br/>
Objeto `_variant_t`.

*clsid*<br/>
El `CLSID` de una coclase.

*dwClsContext*<br/>
Contexto para el código ejecutable.

*lpcStr*<br/>
Una cadena multibyte que contiene un `CLSID` (empezando por "**{**") o un `ProgID`.

*pOuter*<br/>
El desconocido externo para [agregación](/windows/desktop/com/aggregation).

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)