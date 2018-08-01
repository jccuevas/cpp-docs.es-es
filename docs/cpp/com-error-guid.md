---
title: _com_error::GUID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c592607732eb5558ce74edb7b71adbc023b2ae52
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402288"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Específicos de Microsoft**  
  
 Llama a la función `IErrorInfo::GetGUID`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
GUID GUID( ) const throw( );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de `IErrorInfo::GetGUID` para el `IErrorInfo` objeto grabado dentro del `_com_error` objeto. Si no hay ningún `IErrorInfo` se registra el objeto, devuelve `GUID_NULL`.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier error durante la llamada a la `IErrorInfo::GetGUID` se omite el método.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)