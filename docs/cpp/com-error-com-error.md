---
title: _com_error::_com_error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d26239f6edf98e90f9d4d773d654025da410a97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Específicos de Microsoft**  
  
 Construye un objeto `_com_error`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      _com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false  
) throw( );  
_com_error(  
   const _com_error& that   
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hr`  
 Información de `HRESULT`.  
  
 `perrinfo`  
 **IErrorInfo** objeto.  
  
 **BOOL fAddRef = false**  
 Hace que el constructor llame a AddRef en un valor no nulo **IErrorInfo** interfaz. Esto proporciona un recuento de referencias correcto en el caso habitual de que la propiedad de la interfaz se pase al objeto `_com_error`, por ejemplo:  
  
```  
throw _com_error(hr, perrinfo);  
```  
  
 Si no desea que su código para transferir la propiedad a la `_com_error` objeto y el `AddRef` es necesario para compensar la **versión** en el `_com_error` destructor, construya el objeto como sigue:  
  
```  
_com_error err(hr, perrinfo, true);  
```  
  
 `that`  
 Objeto `_com_error` existente.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor crea un nuevo objeto, dados un `HRESULT` y opcionales **IErrorInfo** objeto. El segundo crea una copia de un objeto `_com_error` existente.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)