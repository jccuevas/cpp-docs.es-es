---
title: _com_error::HRESULTToWCode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c39b638451aa8ea89191e323eae5f2c140563990
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082071"
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

*recursos humanos*<br/>
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