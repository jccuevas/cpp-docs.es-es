---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: b3c79bb069ef504680e83359d6ec90c803f16d9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180594"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Específicos de Microsoft**

Llama a la función `IErrorInfo::GetHelpContext`.

## <a name="syntax"></a>Sintaxis

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Devuelve el resultado de `IErrorInfo::GetHelpContext` para el objeto `IErrorInfo` registrado en el objeto `_com_error`. Si no se registra ningún objeto de `IErrorInfo`, devuelve un cero.

## <a name="remarks"></a>Observaciones

Cualquier error que se produzca mientras se llama al método `IErrorInfo::GetHelpContext` se omite.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error (Clase)](../cpp/com-error-class.md)
