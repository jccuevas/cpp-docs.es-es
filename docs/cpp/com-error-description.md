---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: de2275f096fe2fde96e64cbc3034602a1fde5e88
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180776"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Específicos de Microsoft**

Llama a la función `IErrorInfo::GetDescription`.

## <a name="syntax"></a>Sintaxis

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Valor devuelto

Devuelve el resultado de `IErrorInfo::GetDescription` para el objeto `IErrorInfo` registrado en el objeto `_com_error`. El `BSTR` resultante se encapsula en un objeto `_bstr_t`. Si no se registra ningún `IErrorInfo`, devuelve un `_bstr_t`vacío.

## <a name="remarks"></a>Observaciones

Llama a la función `IErrorInfo::GetDescription` y recupera `IErrorInfo` grabadas en el objeto `_com_error`. Cualquier error que se produzca mientras se llama al método `IErrorInfo::GetDescription` se omite.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error (Clase)](../cpp/com-error-class.md)
