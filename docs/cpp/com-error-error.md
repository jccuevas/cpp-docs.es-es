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
ms.openlocfilehash: 010d1b2e10d1435855c35929516ff0e7f3fd8d4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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