---
title: '_com_error:: wcode | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
- WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
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
ms.openlocfilehash: 15c0d860a5faffc160def725630fbbb1d84d8ed8
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorwcode"></a>_com_error::WCode
**Específicos de Microsoft**  
  
 Recupera el código de error de 16 bits asignado en el `HRESULT`encapsulado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si el `HRESULT` está dentro del intervalo 0 x 80040200 a 0x8004FFFF, el **WCode** método devuelve el `HRESULT` menos 0 x 80040200; de lo contrario, devuelve cero.  
  
## <a name="remarks"></a>Comentarios  
 El **WCode** método se usa para deshacer una asignación que tiene lugar en el código de compatibilidad con COM. El contenedor de un **dispinterface** propiedad o un método llama a una rutina de soporte que empaqueta los argumentos y llama **IDispatch:: Invoke**. Al volver, si un error `HRESULT` de `DISP_E_EXCEPTION` se devuelve, se recupera la información de error de la **EXCEPINFO** estructura pasada a **IDispatch:: Invoke**. El código de error puede ser un valor de 16 bits almacenado en el `wCode` miembro de la **EXCEPINFO** estructura o un valor de 32 bits en el **scode** miembro de la **EXCEPINFO**estructura. Si se devuelve un `wCode` de 16 bits, primero debe asignarse a un error `HRESULT` de 32 bits.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error (Clase)](../cpp/com-error-class.md)
