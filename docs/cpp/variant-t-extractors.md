---
title: _variant_t (extractores) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65049a473f62e728fcb4d74b581a08c0f1723fc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="variantt-extractors"></a>_variant_t (Extractores)
**Específicos de Microsoft**  
  
 Extraer datos de encapsulado **VARIANT** objeto.  
  
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
  
## <a name="remarks"></a>Comentarios  
 Extrae datos sin procesar de encapsulado **VARIANT**. Si el **VARIANT** ya no es del tipo adecuado, **VariantChangeType** se usa para intentar la conversión, y se genera un error en caso de error:  
  
-   **operator short ()** extrae un **corto** valor entero.  
  
-   **operator long ()** extrae un **largo** valor entero.  
  
-   **operator float ()** extrae un **float** valor numérico.  
  
-   **operator double ()** extrae un **doble** valor entero.  
  
-   **operator CY ()** extrae un **CY** objeto.  
  
-   **bool (operador)** extrae un `bool` valor.  
  
-   **operator DECIMAL ()** extrae un **DECIMAL** valor.  
  
-   **operator BYTE ()** extrae un **bytes** valor.  
  
-   **_bstr_t (operador)** extrae una cadena, que se encapsula en un `_bstr_t` objeto.  
  
-   **operador IDispatch\*()** extrae un puntero dispinterface de encapsulado **VARIANT**. `AddRef` se llama en el puntero resultante, por lo que es decisión suya llamar a **versión** para liberarlo.  
  
-   **operador IUnknown\*()** extrae un puntero a interfaz COM encapsulado **VARIANT**. `AddRef` se llama en el puntero resultante, por lo que es decisión suya llamar a **versión** para liberarlo.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)
