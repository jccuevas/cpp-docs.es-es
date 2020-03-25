---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 43dd21297ddd54863d535402dddd59243d589eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180529"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Específicos de Microsoft**

Llama a la función `IErrorInfo::GetSource`.

## <a name="syntax"></a>Sintaxis

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Valor devuelto

Devuelve el resultado de `IErrorInfo::GetSource` para el objeto `IErrorInfo` registrado en el objeto `_com_error`. El `BSTR` resultante se encapsula en un objeto `_bstr_t`. Si no se registra ningún `IErrorInfo`, devuelve un `_bstr_t`vacío.

## <a name="remarks"></a>Observaciones

Cualquier error que se produzca mientras se llama al método `IErrorInfo::GetSource` se omite.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error (Clase)](../cpp/com-error-class.md)
