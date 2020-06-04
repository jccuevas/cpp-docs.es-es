---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 8e2c52d10b15822703329dcea18944773f5784ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180763"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Específicos de Microsoft**

Recupera el HRESULT que se pasa al constructor.

## <a name="syntax"></a>Sintaxis

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Elemento HRESULT sin formato pasado en el constructor.

## <a name="remarks"></a>Observaciones

Recupera el elemento HRESULT encapsulado en un objeto `_com_error`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error (Clase)](../cpp/com-error-class.md)
