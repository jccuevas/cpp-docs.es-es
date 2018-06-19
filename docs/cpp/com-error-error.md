---
title: _com_error::error | Documentos de Microsoft
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
ms.openlocfilehash: 02afac78de5eb5908d477f8503ceeebffe46f672
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412587"
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