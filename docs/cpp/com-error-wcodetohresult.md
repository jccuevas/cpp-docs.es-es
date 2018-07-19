---
title: _com_error::WCodeToHRESULT | Microsoft Docs
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
ms.openlocfilehash: dce98775007360e3fdd4177141f7a550548d3679
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939200"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Específicos de Microsoft**  
  
 Mapas de bits de 16 *wCode* HRESULT de 32 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 *WCode*  
 Lo 16 bits *wCode* asignarse a HRESULT de 32 bits.  
  
## <a name="return-value"></a>Valor devuelto  
 HRESULT de 32 bits asignado desde el 16 bits *wCode*.  
  
## <a name="remarks"></a>Comentarios  
 Consulte la [WCode](../cpp/com-error-wcode.md) función miembro.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error (Clase)](../cpp/com-error-class.md)