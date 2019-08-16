---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 13ddf57e0bdbdbcc0c5b487e879e14b000de3ad0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393940"
---
# <a name="bstrtcopy"></a>_bstr_t::copy

**Específicos de Microsoft**

Crea una copia del objeto `BSTR` encapsulado.

## <a name="syntax"></a>Sintaxis

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Parámetros

*fCopy*<br/>
Si es TRUE, **copia** devuelve una copia de los contenidos `BSTR`en caso contrario, **copia** devuelve el objeto BSTR real.

## <a name="remarks"></a>Comentarios

Devuelve una copia recién asignada del objeto `BSTR` encapsulado.

## <a name="example"></a>Ejemplo

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)