---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: a517c40e9adfbda2d790ce41a48ccf8658bcd3e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544396"
---
# <a name="comerrordescription"></a>_com_error::Description

**Específicos de Microsoft**

Llama a la función `IErrorInfo::GetDescription`.

## <a name="syntax"></a>Sintaxis

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Valor devuelto

Devuelve el resultado de `IErrorInfo::GetDescription` para el `IErrorInfo` objeto grabado dentro del `_com_error` objeto. El `BSTR` resultante se encapsula en un objeto `_bstr_t`. Si no hay ningún `IErrorInfo` está registrado, devuelve un valor vacío `_bstr_t`.

## <a name="remarks"></a>Comentarios

Llama a la `IErrorInfo::GetDescription` función y recupera `IErrorInfo` grabado dentro del `_com_error` objeto. Cualquier error durante la llamada a la `IErrorInfo::GetDescription` se omite el método.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error (Clase)](../cpp/com-error-class.md)