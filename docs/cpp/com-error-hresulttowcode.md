---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: d89503e822d92bf6a1fcb2b6bb658d532af32c5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155051"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode

**Específicos de Microsoft**

Asigna el valor HRESULT de 32 bits a 16 bits `wCode`.

## <a name="syntax"></a>Sintaxis

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Parámetros

*hr*<br/>
El valor HRESULT de 32 bits que debe asignarse a 16 bits `wCode`.

## <a name="return-value"></a>Valor devuelto

16 bits `wCode` asignado desde el valor HRESULT de 32 bits.

## <a name="remarks"></a>Comentarios

Consulte [_com_error:: wcode](../cpp/com-error-wcode.md) para obtener más información.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error (Clase)](../cpp/com-error-class.md)