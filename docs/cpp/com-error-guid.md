---
title: _com_error::GUID | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee1952e50251cfac7563357c7626ab8603589e4d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409697"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Específicos de Microsoft**  
  
 Llamadas **IErrorInfo:: GetGuid** función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de **IErrorInfo:: GetGuid** para el **IErrorInfo** objeto registrado dentro del `_com_error` objeto. Si no hay ningún **IErrorInfo** se registra el objeto, devuelve `GUID_NULL`.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier error al llamar a la **IErrorInfo:: GetGuid** método se pasa por alto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)