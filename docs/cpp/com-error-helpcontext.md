---
title: _com_error::HelpContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e800bd3100fa0199534f3e9bdf6646aa0ffc6860
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940903"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Específicos de Microsoft**  
  
 Llama a la función `IErrorInfo::GetHelpContext`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de `IErrorInfo::GetHelpContext` para el `IErrorInfo` objeto grabado dentro del `_com_error` objeto. Si no hay ningún `IErrorInfo` se registra el objeto, éste devuelve un cero.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier error durante la llamada a la `IErrorInfo::GetHelpContext` se omite el método.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)