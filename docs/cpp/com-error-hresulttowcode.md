---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 35a497c273f15c9755d3607e7907a3a48dad8dc8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180568"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Específicos de Microsoft**

Asigna HRESULT de 32 bits a `wCode`de 16 bits.

## <a name="syntax"></a>Sintaxis

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Parámetros

*hora*<br/>
HRESULT de 32 bits que se va a asignar a `wCode`de 16 bits.

## <a name="return-value"></a>Valor devuelto

`wCode` de 16 bits asignado desde el HRESULT de 32 bits.

## <a name="remarks"></a>Observaciones

Vea [_com_error:: WCode](../cpp/com-error-wcode.md) para obtener más información.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error (Clase)](../cpp/com-error-class.md)
