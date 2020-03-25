---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 1fe8cfb5b644b3c7c34cf3325a91ebdf23a04946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190331"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Específicos de Microsoft**

Crea una copia del objeto `BSTR` encapsulado.

## <a name="syntax"></a>Sintaxis

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Parámetros

*fCopy*<br/>
Si es TRUE, **Copy** devuelve una copia del `BSTR`contenido; de lo contrario, **Copy** devuelve el BSTR real.

## <a name="remarks"></a>Observaciones

Devuelve una copia recién asignada del objeto `BSTR` encapsulado.

## <a name="example"></a>Ejemplo

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)
