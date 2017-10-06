---
title: _com_error::ErrorInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: e80dafb5d1472ec28631b13ab05a0dea0b4de4ba
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
