---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 826ac53f001355127f16b7ad2a7583a0f8800de7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155038"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile

**Específicos de Microsoft**

Llama a la función `IErrorInfo::GetHelpFile`.

## <a name="syntax"></a>Sintaxis

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Valor devuelto

Devuelve el resultado de `IErrorInfo::GetHelpFile` para el `IErrorInfo` objeto grabado dentro del `_com_error` objeto. El BSTR resultante se encapsula en un objeto `_bstr_t`. Si no hay ningún `IErrorInfo` está registrado, devuelve un valor vacío `_bstr_t`.

## <a name="remarks"></a>Comentarios

Cualquier error durante la llamada a la `IErrorInfo::GetHelpFile` se omite el método.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error (Clase)](../cpp/com-error-class.md)