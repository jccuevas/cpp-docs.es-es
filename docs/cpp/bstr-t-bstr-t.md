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
ms.openlocfilehash: 70678b0be8b25bf3ee883630caa26598e5e31089
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450081"
---
# <a name="bstrtbstrt"></a>_bstr_t::_bstr_t

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
Un [_variant_t](../cpp/variant-t-class.md) objeto.

*BSTR*<br/>
Objeto `BSTR` existente.

*fCopy*<br/>
Si es FALSE, el *bstr* argumento se adjunta al nuevo objeto sin crear una copia mediante una llamada a `SysAllocString`.

## <a name="remarks"></a>Comentarios

En la siguiente tabla se describen los constructores `_bstr_t`.

|Constructor|Descripción|
|-----------------|-----------------|
|`_bstr_t( )`|Construye un valor predeterminado `_bstr_t` objeto que encapsula un valor null `BSTR` objeto.|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Construye un objeto `_bstr_t` como copia de otro.<br /><br /> Se trata de un *superficial* copia, lo que incrementa el recuento de referencias de encapsulado `BSTR` objeto en lugar de crear uno nuevo.|
|`_bstr_t( char*`  `s2`  `)`|Construye un objeto `_bstr_t` mediante una llamada a `SysAllocString` para crear un nuevo objeto `BSTR` y, a continuación, lo encapsula.<br /><br /> Este constructor realiza primero una conversión de multibyte a Unicode.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Construye un objeto `_bstr_t` mediante una llamada a `SysAllocString` para crear un nuevo objeto `BSTR` y, a continuación, lo encapsula.|
|`_bstr_t( _variant_t&`  `var`  `)`|Construye un objeto `_bstr_t` a partir de un objeto `_variant_t`: primero recupera un objeto `BSTR` del objeto VARIANT encapsulado.|
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Construye un objeto `_bstr_t` a partir de un objeto `BSTR` existente (en lugar de una cadena `wchar_t*`). Si *fCopy* es false, proporcionado `BSTR` se adjunta al nuevo objeto sin crear una nueva copia con `SysAllocString`.<br /><br /> Las funciones contenedoras usan este constructor en los encabezados de la biblioteca de tipos para encapsular y tomar la propiedad de un objeto `BSTR` devuelto por un método de interfaz.|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)<br/>
[_variant_t (Clase)](../cpp/variant-t-class.md)