---
title: '_com_error:: wcode | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9ad0cbfa614c132a75e25f46b34e37ec3a5fc64
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407009"
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Específicos de Microsoft**  
  
 Recupera el código de error de 16 bits asignado en el valor de HRESULT encapsulado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WORD WCode ( ) const throw( );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si el valor HRESULT está dentro del intervalo 0 x 80040200 a 0x8004FFFF, el `WCode` método devuelve el valor HRESULT menos 0 x 80040200; de lo contrario, devuelve cero.  
  
## <a name="remarks"></a>Comentarios  
 El `WCode` método se usa para deshacer una asignación que ocurre en el código de soporte COM. El contenedor para un `dispinterface` propiedad o método llama a una rutina de soporte que empaqueta los argumentos y las llamadas `IDispatch::Invoke`. Cuando se devuelve, si un valor HRESULT de error de `DISP_E_EXCEPTION` se devuelve la información de error se recupera de la `EXCEPINFO` estructura pasada a `IDispatch::Invoke`. El código de error puede ser un valor de 16 bits almacenado en el `wCode` miembro de la `EXCEPINFO` estructura o un valor de 32 bits en el `scode` miembro de la `EXCEPINFO` estructura. Si los 16 bits `wCode` se devuelve, en primer lugar debe asignarse a un valor HRESULT de error de 32 bits.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error (Clase)](../cpp/com-error-class.md)