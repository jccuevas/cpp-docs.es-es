---
title: _variant_t (Extractores)
ms.date: 11/04/2016
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
ms.openlocfilehash: 685df7285e58e0cf2ceeded5ac27641364897298
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187705"
---
# <a name="_variant_t-extractors"></a>_variant_t (Extractores)

**Específicos de Microsoft**

Extrae datos del objeto `VARIANT` encapsulado.

## <a name="syntax"></a>Sintaxis

```
operator short( ) const;
operator long( ) const;
operator float( ) const;
operator double( ) const;
operator CY( ) const;
operator _bstr_t( ) const;
operator IDispatch*( ) const;
operator bool( ) const;
operator IUnknown*( ) const;
operator DECIMAL( ) const;
operator BYTE( ) const;
operator VARIANT() const throw();
operator char() const;
operator unsigned short() const;
operator unsigned long() const;
operator int() const;
operator unsigned int() const;
operator __int64() const;
operator unsigned __int64() const;
```

## <a name="remarks"></a>Observaciones

Extrae datos sin procesar de una `VARIANT`encapsulada. Si el `VARIANT` todavía no es el tipo adecuado, `VariantChangeType` se utiliza para intentar una conversión y se genera un error en caso de error:

- **operador Short ()** Extrae un valor entero **corto** .

- **operador Long ()** Extrae un valor entero **largo** .

- **Operator Float ()** Extrae un valor numérico **float** .

- **Operator Double ()** Extrae un valor entero **Double** .

- **operador CY ()** Extrae un objeto `CY`.

- **Operator bool ()** Extrae un valor **bool** .

- **Operator decimal ()** Extrae un valor de `DECIMAL`.

- **operador byte ()** Extrae un valor de `BYTE`.

- **operador _bstr_t ()** Extrae una cadena, que se encapsula en un objeto `_bstr_t`.

- **operador IDispatch\*()** Extrae un puntero dispinterface de una `VARIANT`encapsulada. en el puntero resultante se llama a `AddRef`, por lo que depende de usted llamar a `Release` para liberarlo.

- **operador IUnknown\*()** Extrae un puntero de interfaz COM de un `VARIANT`encapsulado. en el puntero resultante se llama a `AddRef`, por lo que depende de usted llamar a `Release` para liberarlo.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_variant_t (Clase)](../cpp/variant-t-class.md)
