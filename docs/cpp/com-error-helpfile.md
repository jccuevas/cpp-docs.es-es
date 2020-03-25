---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 775adfa7d5dd5aca098edcd793c2164d65fe7efa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190227"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Específicos de Microsoft**

Llama a la función `IErrorInfo::GetHelpFile`.

## <a name="syntax"></a>Sintaxis

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Valor devuelto

Devuelve el resultado de `IErrorInfo::GetHelpFile` para el objeto `IErrorInfo` registrado en el objeto `_com_error`. El BSTR resultante se encapsula en un objeto `_bstr_t`. Si no se registra ningún `IErrorInfo`, devuelve un `_bstr_t`vacío.

## <a name="remarks"></a>Observaciones

Cualquier error que se produzca mientras se llama al método `IErrorInfo::GetHelpFile` se omite.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error (Clase)](../cpp/com-error-class.md)
