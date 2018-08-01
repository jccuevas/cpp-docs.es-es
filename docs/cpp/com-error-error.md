---
title: _com_error::error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7ddaefcf3bd46bf40b03c03d2d1fb00cf8fbbb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408432"
---
# <a name="comerrorerror"></a>_com_error::Error
**Específicos de Microsoft**  
  
 Recupera el valor HRESULT pasado al constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Error( ) const throw( );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Elemento HRESULT sin formato pasado al constructor.  
  
## <a name="remarks"></a>Comentarios  
 Recupera el elemento HRESULT encapsulado en un `_com_error` objeto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)