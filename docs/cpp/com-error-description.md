---
title: _com_error::Description | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 848709fa6cbbbfb4166750f86540de2433a73023
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404033"
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