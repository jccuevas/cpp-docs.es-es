---
title: '_com_error:: wcode | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::WCode
dev_langs: C++
helpviewer_keywords: WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 74f79491b9d4f88e19bcd0f7a20c94b26d0f7909
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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