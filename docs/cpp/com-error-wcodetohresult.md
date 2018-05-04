---
title: _com_error::WCodeToHRESULT | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCodeToHRESULT
dev_langs:
- C++
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31b9df8305d0eea772979904f63847f6d6c2325a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Específicos de Microsoft**  
  
 Mapas de bits de 16 `wCode` a 32 bits `HRESULT`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `wCode`  
 `wCode` de 16 bits que se asignará a `HRESULT` de 32 bits.  
  
## <a name="return-value"></a>Valor devuelto  
 `HRESULT` de 32 bits asignado desde `wCode` de 16 bits.  
  
## <a name="remarks"></a>Comentarios  
 Consulte la [WCode](../cpp/com-error-wcode.md) función miembro.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error (Clase)](../cpp/com-error-class.md)