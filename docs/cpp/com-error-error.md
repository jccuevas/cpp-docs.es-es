---
title: _com_error::error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs: C++
helpviewer_keywords: Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a318ba69fe5e5d19bacb6d5890889d31a5a44d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorerror"></a>_com_error::Error
**Específicos de Microsoft**  
  
 Recupera el `HRESULT` pasado al constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT Error( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Elemento `HRESULT` sin formato pasado en el constructor.  
  
## <a name="remarks"></a>Comentarios  
 Recupera el elemento `HRESULT` encapsulado de un objeto `_com_error`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)