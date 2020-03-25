---
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: 402251592a87b723d75fd1b2cd0786be7b17dbfc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187627"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Específicos de Microsoft**

## <a name="syntax"></a>Sintaxis

```
_variant_t& operator=(
   const VARIANT& varSrc
);

_variant_t& operator=(
   const VARIANT* pVarSrc
);

_variant_t& operator=(
   const _variant_t& var_t_Src
);

_variant_t& operator=(
   short sSrc
);

_variant_t& operator=(
   long lSrc
);

_variant_t& operator=(
   float fltSrc
);

_variant_t& operator=(
   double dblSrc
);

_variant_t& operator=(
   const CY& cySrc
);

_variant_t& operator=(
   const _bstr_t& bstrSrc
);

_variant_t& operator=(
   const wchar_t* wstrSrc
);

_variant_t& operator=(
   const char* strSrc
);

_variant_t& operator=(
   IDispatch* pDispSrc
);

_variant_t& operator=(
   bool bSrc
);

_variant_t& operator=(
   IUnknown* pSrc
);

_variant_t& operator=(
   const DECIMAL& decSrc
);

_variant_t& operator=(
   BYTE bSrc
);

_variant_t& operator=(
   char cSrc
);

_variant_t& operator=(
   unsigned short usSrc
);

_variant_t& operator=(
   unsigned long ulSrc
);

_variant_t& operator=(
   int iSrc
);

_variant_t& operator=(
   unsigned int uiSrc
);

_variant_t& operator=(
   __int64 i8Src
);

_variant_t& operator=(
   unsigned __int64 ui8Src
);
```

## <a name="remarks"></a>Observaciones

El operador asigna un nuevo valor al objeto `_variant_t`:

- **Operator = (**  *varSrc*  **)** Asigna un `VARIANT` existente a un objeto `_variant_t`.

- **Operator = (**  *pVarSrc*  **)** Asigna un `VARIANT` existente a un objeto `_variant_t`.

- **Operator = (**  *var_t_Src*  **)** Asigna un objeto de `_variant_t` existente a un objeto `_variant_t`.

- **Operator = (**  *sSrc*  **)** Asigna un valor entero **corto** a un objeto `_variant_t`.

- **Operator = (** `lSrc` **)** Asigna un valor entero **largo** a un objeto `_variant_t`.

- **Operator = (**  *fltSrc*  **)** Asigna un valor numérico **float** a un objeto `_variant_t`.

- **Operator = (**  *dblSrc*  **)** Asigna un valor numérico **doble** a un objeto `_variant_t`.

- **Operator = (**  *cySrc*  **)** Asigna un objeto `CY` a un objeto `_variant_t`.

- **Operator = (**  *bstrSrc*  **)** Asigna un objeto `BSTR` a un objeto `_variant_t`.

- **Operator = (**  *wstrSrc*  **)** Asigna una cadena Unicode a un objeto `_variant_t`.

- **Operator = (** `strSrc` **)** Asigna una cadena multibyte a un objeto `_variant_t`.

- **Operator = (** `bSrc` **)** Asigna un valor **booleano** a un objeto `_variant_t`.

- **Operator = (**  *pDispSrc*  **)** Asigna un objeto `VT_DISPATCH` a un objeto `_variant_t`.

- **Operator = (**  *pIUnknownSrc*  **)** Asigna un objeto `VT_UNKNOWN` a un objeto `_variant_t`.

- **Operator = (**  *decSrc*  **)** Asigna un valor de `DECIMAL` a un objeto `_variant_t`.

- **Operator = (** `bSrc` **)** Asigna un valor de `BYTE` a un objeto `_variant_t`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_variant_t (Clase)](../cpp/variant-t-class.md)
