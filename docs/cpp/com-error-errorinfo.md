---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: cedb9ccadc63166c43d980333d93a195254700d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180711"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Específicos de Microsoft**

Recupera el objeto `IErrorInfo` pasado al constructor.

## <a name="syntax"></a>Sintaxis

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Elemento `IErrorInfo` sin formato pasado en el constructor.

## <a name="remarks"></a>Observaciones

Recupera el elemento de `IErrorInfo` encapsulado en un objeto `_com_error` o NULL si no se registra ningún elemento `IErrorInfo`. El llamador debe llamar a `Release` en el objeto devuelto cuando termine de usarlo.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error (Clase)](../cpp/com-error-class.md)
