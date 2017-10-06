---
title: _com_error::HRESULTToWCode | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
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
ms.openlocfilehash: 296c6f43c1bc840ae13bdf4ad355d7f41e2cc3fd
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
