---
title: _com_error::_com_error | Microsoft Docs
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
ms.openlocfilehash: ec16faa9881fc1c69dca5f8f39b8797cf0fcff0d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944474"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Específicos de Microsoft**  
  
 Construye un objeto `_com_error`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
_com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false) throw( );  

_com_error( const _com_error& that ) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 *recursos humanos*  
 Información de HRESULT.  
  
 *perrinfo*  
 Objeto `IErrorInfo`.  
  
 `bool fAddRef=false`  
 Hace que el constructor llame a AddRef en un valor no null `IErrorInfo` interfaz. Esto proporciona un recuento de referencias correcto en el caso habitual de que la propiedad de la interfaz se pase al objeto `_com_error`, por ejemplo:  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 Si no desea que su código para transferir la propiedad a la `_com_error` objeto y el `AddRef` es necesario para desplazar el `Release` en el `_com_error` destructor, construya el objeto como sigue:  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *que*  
 Objeto `_com_error` existente.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor crea un nuevo objeto, dados un HRESULT y opcional `IErrorInfo` objeto. El segundo crea una copia de un objeto `_com_error` existente.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)