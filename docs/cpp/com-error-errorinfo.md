---
title: _com_error::ErrorInfo | Documentos de Microsoft
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
ms.openlocfilehash: 8fbc735dfae1b30209eccfd14f1170826fb07680
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Específicos de Microsoft**  
  
 Recupera el **IErrorInfo** objeto pasado al constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Sin formato **IErrorInfo** elemento pasado al constructor.  
  
## <a name="remarks"></a>Comentarios  
 Recupera el objeto encapsulado **IErrorInfo** de elemento en un `_com_error` objeto, o **NULL** si no hay ningún **IErrorInfo** se registra el elemento. El llamador debe llamar a **versión** en el objeto devuelto cuando terminado de usarlo.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)