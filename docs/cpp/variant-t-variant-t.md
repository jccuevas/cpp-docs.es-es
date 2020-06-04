---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: fff116ef04967a1887eaa075d92d3ea0283d5427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187536"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Específicos de Microsoft**

Construye un objeto `_variant_t`.

## <a name="syntax"></a>Sintaxis

```
_variant_t( ) throw( );

_variant_t(
   const VARIANT& varSrc
);

_variant_t(
   const VARIANT* pVarSrc
);

_variant_t(
   const _variant_t& var_t_Src
);

_variant_t(
   VARIANT& varSrc,
   bool fCopy
);

_variant_t(
   short sSrc,
   VARTYPE vtSrc = VT_I2
);

_variant_t(
   long lSrc,
   VARTYPE vtSrc = VT_I4
);

_variant_t(
   float fltSrc
) throw( );

_variant_t(
   double dblSrc,
   VARTYPE vtSrc = VT_R8
);

_variant_t(
   const CY& cySrc
) throw( );

_variant_t(
   const _bstr_t& bstrSrc
);

_variant_t(
   const wchar_t *wstrSrc
);

_variant_t(
   const char* strSrc
);

_variant_t(
   IDispatch* pDispSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   bool bSrc
) throw( );

_variant_t(
   IUnknown* pIUknownSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   const DECIMAL& decSrc
) throw( );

_variant_t(
   BYTE bSrc
) throw( );

variant_t(
   char cSrc
) throw();

_variant_t(
   unsigned short usSrc
) throw();

_variant_t(
   unsigned long ulSrc
) throw();

_variant_t(
   int iSrc
) throw();

_variant_t(
   unsigned int uiSrc
) throw();

_variant_t(
   __int64 i8Src
) throw();

_variant_t(
   unsigned __int64 ui8Src
) throw();
```

#### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Un objeto `VARIANT` que se va a copiar en el nuevo objeto `_variant_t`.

*pVarSrc*<br/>
Puntero a un objeto `VARIANT` que se va a copiar en el nuevo objeto `_variant_t`.

*var_t_Src*<br/>
Un objeto `_variant_t` que se va a copiar en el nuevo objeto `_variant_t`.

*fCopy*<br/>
Si es **false**, el objeto de `VARIANT` proporcionado se adjunta al nuevo objeto `_variant_t` sin crear una nueva copia de `VariantCopy`.

*ISrc, sSrc*<br/>
Un valor entero que se va a copiar en el nuevo objeto `_variant_t`.

*vtSrc*<br/>
`VARTYPE` del nuevo objeto `_variant_t`.

*fltSrc, dblSrc*<br/>
Un valor numérico que se va a copiar en el nuevo objeto `_variant_t`.

*cySrc*<br/>
Un objeto `CY` que se va a copiar en el nuevo objeto `_variant_t`.

*bstrSrc*<br/>
Un objeto `_bstr_t` que se va a copiar en el nuevo objeto `_variant_t`.

*strSrc, wstrSrc*<br/>
Una cadena que se va a copiar en el nuevo objeto `_variant_t`.

*bSrc*<br/>
Valor **booleano** que se va a copiar en el nuevo objeto de `_variant_t`.

*pIUknownSrc*<br/>
Puntero de interfaz COM a un objeto VT_UNKNOWN que se va a encapsular en el nuevo objeto `_variant_t`.

*pDispSrc*<br/>
Puntero de interfaz COM a un objeto VT_DISPATCH que se va a encapsular en el nuevo objeto `_variant_t`.

*decSrc*<br/>
Un valor `DECIMAL` que se va a copiar en el nuevo objeto `_variant_t`.

*bSrc*<br/>
Un valor `BYTE` que se va a copiar en el nuevo objeto `_variant_t`.

*cSrc*<br/>
Valor **Char** que se va a copiar en el nuevo objeto `_variant_t`.

*usSrc*<br/>
Valor **Short sin signo** que se va a copiar en el nuevo objeto de `_variant_t`.

*ulSrc*<br/>
Valor **Long sin signo** que se va a copiar en el nuevo objeto de `_variant_t`.

*iSrc*<br/>
Valor **int** que se va a copiar en el nuevo objeto de `_variant_t`.

*uiSrc*<br/>
Valor **int sin signo** que se va a copiar en el nuevo objeto de `_variant_t`.

*i8Src*<br/>
Un valor **__int64** que se va a copiar en el nuevo objeto `_variant_t`.

*ui8Src*<br/>
Un valor de **__int64 sin signo** que se va a copiar en el nuevo objeto `_variant_t`.

## <a name="remarks"></a>Observaciones

- **_variant_t ()** Construye un objeto de `_variant_t` vacío, `VT_EMPTY`.

- **_variant_t (variant &**  *varSrc*  **)** Construye un objeto `_variant_t` a partir de una copia del objeto `VARIANT`. El tipo variant se conserva.

- **_variant_t (variant** <strong>\*</strong> *pVarSrc* **)** Construye un objeto `_variant_t` a partir de una copia del objeto `VARIANT`. El tipo variant se conserva.

- **_variant_t (_variant_t &**  *var_t_Src*  **)** Construye un objeto `_variant_t` a partir de otro objeto `_variant_t`. El tipo variant se conserva.

- **_variant_t (variant &** *varSrc* **, bool**`fCopy` **)** Construye un objeto de `_variant_t` a partir de un objeto de `VARIANT` existente. Si *fCopy* es **false**, el objeto **Variant** se adjunta al nuevo objeto sin crear una copia.

- **_variant_t (Short***sSrc* **, VARTYPE**`vtSrc` **= VT_I2)** Construye un objeto de `_variant_t` de tipo VT_I2 o VT_BOOL a partir de un valor entero **corto** . Cualquier otro `VARTYPE` produce un error de E_INVALIDARG.

- **_variant_t (long**`lSrc` **, VARTYPE**`vtSrc` **= VT_I4)** Construye un objeto de `_variant_t` de tipo VT_I4, VT_BOOL o VT_ERROR a partir de un valor entero **largo** . Cualquier otro `VARTYPE` produce un error de E_INVALIDARG.

- **_variant_t (float**`fltSrc` **)** Construye un objeto de `_variant_t` de tipo VT_R4 a partir de un valor numérico **float** .

- **_variant_t (double**`dblSrc` **, VARTYPE**`vtSrc` **= VT_R8)** Construye un objeto de `_variant_t` de tipo VT_R8 o VT_DATE a partir de un valor numérico **doble** . Cualquier otro `VARTYPE` produce un error de E_INVALIDARG.

- **_variant_t (`cySrc`CY &** **)** Construye un objeto de `_variant_t` de tipo VT_CY a partir de un objeto `CY`.

- **_variant_t (_bstr_t &** `bstrSrc` **)** Construye un objeto de `_variant_t` de tipo VT_BSTR a partir de un objeto `_bstr_t`. Se asigna un nuevo `BSTR`.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc*  **)** Construye un objeto de `_variant_t` de tipo VT_BSTR a partir de una cadena Unicode. Se asigna un nuevo `BSTR`.

- **_variant_t (char** <strong>\*</strong>`strSrc` **)** Construye un objeto de `_variant_t` de tipo VT_BSTR a partir de una cadena. Se asigna un nuevo `BSTR`.

- **_variant_t (bool**`bSrc` **)** Construye un objeto de `_variant_t` de tipo VT_BOOL a partir de un valor **booleano** .

- **_variant_t (IUnknown** <strong>\*</strong>`pIUknownSrc` **, bool**`fAddRef` **= true)** Construye un objeto de `_variant_t` de tipo VT_UNKNOWN a partir de un puntero de interfaz COM. Si `fAddRef` es **true**, se llama a `AddRef` en el puntero de interfaz proporcionado para que coincida con la llamada a `Release` que se producirá cuando se destruya el objeto de `_variant_t`. Depende de usted llamar a `Release` en el puntero de interfaz proporcionado. Si `fAddRef` es **false**, este constructor toma la propiedad del puntero de interfaz proporcionado; no llame a `Release` en el puntero de interfaz proporcionado.

- **_variant_t (IDispatch** <strong>\*</strong>`pDispSrc` **, bool**`fAddRef` **= true)** Construye un objeto de `_variant_t` de tipo VT_DISPATCH a partir de un puntero de interfaz COM. Si `fAddRef` es **true**, se llama a `AddRef` en el puntero de interfaz proporcionado para que coincida con la llamada a `Release` que se producirá cuando se destruya el objeto de `_variant_t`. Depende de usted llamar a `Release` en el puntero de interfaz proporcionado. Si `fAddRef` es **false**, este constructor toma la propiedad del puntero de interfaz proporcionado; no llame a `Release` en el puntero de interfaz proporcionado.

- **_variant_t (`decSrc`de &AMP; decimal** **)** Construye un objeto de `_variant_t` de tipo VT_DECIMAL a partir de un valor de `DECIMAL`.

- **_variant_t (BYTE**`bSrc` **)** Construye un objeto de `_variant_t` de tipo `VT_UI1` a partir de un valor de `BYTE`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_variant_t (Clase)](../cpp/variant-t-class.md)
