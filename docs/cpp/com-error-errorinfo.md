---
title: _com_error::ErrorInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc2906827e6a465106a3dbdcb8b63c7b53a39ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039353"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Específicos de Microsoft**

Recupera el objeto `IErrorInfo` pasado al constructor.

## <a name="syntax"></a>Sintaxis

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Elemento `IErrorInfo` sin formato pasado en el constructor.

## <a name="remarks"></a>Comentarios

Recupera el encapsulado `IErrorInfo` de elemento en un `_com_error` objeto, o NULL si no hay ningún `IErrorInfo` se registra el elemento. El llamador debe llamar a `Release` en el objeto devuelto cuando terminado de usarlo.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error (Clase)](../cpp/com-error-class.md)