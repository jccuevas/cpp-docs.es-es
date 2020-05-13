---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: d5b05cd4e26f89d42ea23b605f5e6560795a0cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180646"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Específicos de Microsoft**

Llama a la función `IErrorInfo::GetGUID`.

## <a name="syntax"></a>Sintaxis

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Devuelve el resultado de `IErrorInfo::GetGUID` para el objeto `IErrorInfo` registrado en el objeto `_com_error`. Si no se registra ningún objeto de `IErrorInfo`, devuelve `GUID_NULL`.

## <a name="remarks"></a>Observaciones

Cualquier error que se produzca mientras se llama al método `IErrorInfo::GetGUID` se omite.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error (Clase)](../cpp/com-error-class.md)
