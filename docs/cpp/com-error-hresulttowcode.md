---
title: _com_error::HRESULTToWCode | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e3955fcda665e08e5415652a1e8f1f232d0fe13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Específicos de Microsoft**  
  
 Asigna un `HRESULT` de 32 bits a un `wCode` de 16 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hr`  
 32 bits `HRESULT` que debe asignarse a 16 bits `wCode`.  
  
## <a name="return-value"></a>Valor devuelto  
 16 bits `wCode` asignado de 32 bits `HRESULT`.  
  
## <a name="remarks"></a>Comentarios  
 Vea [_com_error:: wcode](../cpp/com-error-wcode.md) para obtener más información.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error (Clase)](../cpp/com-error-class.md)