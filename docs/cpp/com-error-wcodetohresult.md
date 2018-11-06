---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2fc84be53d95754d21c30eaea8dd981447453d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593076"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Específicos de Microsoft**

Mapas de bits de 16 *wCode* HRESULT de 32 bits.

## <a name="syntax"></a>Sintaxis

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Parámetros

*WCode*<br/>
Lo 16 bits *wCode* asignarse a HRESULT de 32 bits.

## <a name="return-value"></a>Valor devuelto

HRESULT de 32 bits asignado desde el 16 bits *wCode*.

## <a name="remarks"></a>Comentarios

Consulte la [WCode](../cpp/com-error-wcode.md) función miembro.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error (Clase)](../cpp/com-error-class.md)