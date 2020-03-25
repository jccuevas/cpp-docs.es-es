---
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: 3384da733586c828496a8728a0f5855f92eeec35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190474"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Específicos de Microsoft**

Construye un objeto `_bstr_t`.

## <a name="syntax"></a>Sintaxis

```
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

#### <a name="parameters"></a>Parámetros

*s1*<br/>
Objeto `_bstr_t` que se va a copiar.

*s2*<br/>
Cadena multibyte.

*S3*<br/>
Cadena Unicode.

*var*<br/>
Objeto [_variant_t](../cpp/variant-t-class.md) .

*utilicen*<br/>
Objeto `BSTR` existente.

*fCopy*<br/>
Si es FALSE, el argumento *BSTR* se adjunta al nuevo objeto sin realizar una copia mediante una llamada a `SysAllocString`.

## <a name="remarks"></a>Observaciones

En la siguiente tabla se describen los constructores `_bstr_t`.

|Constructor|Descripción|
|-----------------|-----------------|
|`_bstr_t( )`|Construye un objeto `_bstr_t` predeterminado que encapsula un objeto `BSTR` nulo.|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Construye un objeto `_bstr_t` como copia de otro.<br /><br /> Se trata de una copia *superficial* , que incrementa el recuento de referencias del objeto `BSTR` encapsulado en lugar de crear uno nuevo.|
|`_bstr_t( char*`  `s2`  `)`|Construye un objeto `_bstr_t` mediante una llamada a `SysAllocString` para crear un nuevo objeto `BSTR` y, a continuación, lo encapsula.<br /><br /> Este constructor realiza primero una conversión de multibyte a Unicode.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Construye un objeto `_bstr_t` mediante una llamada a `SysAllocString` para crear un nuevo objeto `BSTR` y, a continuación, lo encapsula.|
|`_bstr_t( _variant_t&`  `var`  `)`|Construye un objeto `_bstr_t` a partir de un objeto `_variant_t`: primero recupera un objeto `BSTR` del objeto VARIANT encapsulado.|
|`_bstr_t( BSTR``bstr` `, bool``fCopy``)`|Construye un objeto `_bstr_t` a partir de un objeto `BSTR` existente (en lugar de una cadena `wchar_t*`). Si *fCopy* es false, el `BSTR` proporcionado se adjunta al nuevo objeto sin crear una nueva copia con `SysAllocString`.<br /><br /> Las funciones contenedoras usan este constructor en los encabezados de la biblioteca de tipos para encapsular y tomar la propiedad de un objeto `BSTR` devuelto por un método de interfaz.|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)<br/>
[_variant_t (Clase)](../cpp/variant-t-class.md)
