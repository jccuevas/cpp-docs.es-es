---
title: _bstr_t::_bstr_t | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::_bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 824108b78ede3999a83b1c7c1ac75cc847f182f5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
 `s1`  
 Objeto `_bstr_t` que se va a copiar.  
  
 `s2`  
 Cadena multibyte.  
  
 `s3`  
 Cadena Unicode.  
  
 `var`  
 A [_variant_t](../cpp/variant-t-class.md) objeto.  
  
 `bstr`  
 Objeto `BSTR` existente.  
  
 `fCopy`  
 Si es `false`, el argumento `bstr` se adjunta al nuevo objeto sin crear una copia mediante una llamada a `SysAllocString`.  
  
## <a name="remarks"></a>Comentarios  
 En la siguiente tabla se describen los constructores `_bstr_t`.  
  
|Constructor|Descripción|  
|-----------------|-----------------|  
|`_bstr_t( )`|Construye un valor predeterminado `_bstr_t` objeto que encapsula un valor null `BSTR` objeto.|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|Construye un objeto `_bstr_t` como copia de otro.<br /><br /> Se trata de un *superficial* copia, lo que incrementa el recuento de referencias de encapsulado `BSTR` objeto en lugar de crear uno nuevo.|  
|`_bstr_t( char*`  `s2`  `)`|Construye un objeto `_bstr_t` mediante una llamada a `SysAllocString` para crear un nuevo objeto `BSTR` y, a continuación, lo encapsula.<br /><br /> Este constructor realiza primero una conversión de multibyte a Unicode.|  
|`_bstr_t( wchar_t*`  `s3`  `)`|Construye un objeto `_bstr_t` mediante una llamada a `SysAllocString` para crear un nuevo objeto `BSTR` y, a continuación, lo encapsula.|  
|`_bstr_t( _variant_t&`  `var`  `)`|Construye un objeto `_bstr_t` a partir de un objeto `_variant_t`: primero recupera un objeto `BSTR` del objeto VARIANT encapsulado.|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Construye un objeto `_bstr_t` a partir de un objeto `BSTR` existente (en lugar de una cadena `wchar_t*`). Si `fCopy` es false, el objeto `BSTR` proporcionado se adjunta al nuevo objeto sin crear una nueva copia con `SysAllocString`.<br /><br /> Las funciones contenedoras usan este constructor en los encabezados de la biblioteca de tipos para encapsular y tomar la propiedad de un objeto `BSTR` devuelto por un método de interfaz.|  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (clase)](../cpp/bstr-t-class.md)   
 [_variant_t (Clase)](../cpp/variant-t-class.md)