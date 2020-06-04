---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2194e0e54a93d3227b84d893f9d3f208d972d09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180516"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Específicos de Microsoft**

Asigna *wCode* de 16 bits al HRESULT de 32 bits.

## <a name="syntax"></a>Sintaxis

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Parámetros

*wCode*<br/>
*WCode* de 16 bits que se va a asignar al HRESULT de 32 bits.

## <a name="return-value"></a>Valor devuelto

HRESULT de 32 bits asignado desde el *wCode*de 16 bits.

## <a name="remarks"></a>Observaciones

Vea la función miembro [WCode](../cpp/com-error-wcode.md) .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error (Clase)](../cpp/com-error-class.md)
