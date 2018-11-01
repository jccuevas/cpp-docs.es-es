---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: a421a7fd7fa0817c74dac66946e28928b2ad82dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648713"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext

**Específicos de Microsoft**

Llama a la función `IErrorInfo::GetHelpContext`.

## <a name="syntax"></a>Sintaxis

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Devuelve el resultado de `IErrorInfo::GetHelpContext` para el `IErrorInfo` objeto grabado dentro del `_com_error` objeto. Si no hay ningún `IErrorInfo` se registra el objeto, éste devuelve un cero.

## <a name="remarks"></a>Comentarios

Cualquier error durante la llamada a la `IErrorInfo::GetHelpContext` se omite el método.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error (Clase)](../cpp/com-error-class.md)