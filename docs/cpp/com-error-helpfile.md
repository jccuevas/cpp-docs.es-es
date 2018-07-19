---
title: _com_error::HelpFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acd909224d6a682a210e15eebf04d2c8429a8a3c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939563"
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