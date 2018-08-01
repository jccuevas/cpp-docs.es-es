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
ms.openlocfilehash: c1389635c3ef026e8b3a7dfe13976cca58a15a82
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406723"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Específicos de Microsoft**  
  
 Construye un **_com_error** objeto.  
  
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
 Hace que el constructor llame a AddRef en un valor no null `IErrorInfo` interfaz. Esto proporciona para referencia correcta de recuento en el caso habitual donde la propiedad de la interfaz se pasa a la **_com_error** objetos, como:  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 Si no desea que su código para transferir la propiedad a la **_com_error** objeto y el `AddRef` es necesario para desplazar el `Release` en el **_com_error** destructor, construya el objeto como se indica a continuación:  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *que*  
 Existente **_com_error** objeto.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor crea un nuevo objeto, dados un HRESULT y opcional `IErrorInfo` objeto. El segundo crea una copia de una existente **_com_error** objeto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)