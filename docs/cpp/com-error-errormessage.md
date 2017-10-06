---
title: _com_error::ErrorMessage | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- ErrorMessage method
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
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
ms.openlocfilehash: 01f244a07e46c70cbd4810af666f55dc899e5c3a
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Específicos de Microsoft**  
  
 Recupera el mensaje de cadena para `HRESULT` almacenado en el objeto `_com_error`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el mensaje de cadena para `HRESULT` grabado dentro del objeto `_com_error`. Si el `HRESULT` es un 16 bits asignado [wCode](../cpp/com-error-wcode.md), a continuación, un mensaje genérico "`IDispatch error #<wCode>`" se devuelve. Si no se encuentra ningún mensaje, se devuelve un mensaje genérico “`Unknown error #<hresult>`”. La cadena devuelta es Unicode o cadena multibyte, dependiendo del estado de la **_UNICODE** macro.  
  
## <a name="remarks"></a>Comentarios  
 Recupera el texto del mensaje del sistema adecuado para el `HRESULT` grabado dentro del objeto `_com_error`. El texto del mensaje del sistema se obtiene mediante una llamada a Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) función. La API `FormatMessage` asigna la cadena devuelta, que se libera cuando se destruye el objeto `_com_error`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)
