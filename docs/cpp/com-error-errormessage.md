---
title: _com_error::ErrorMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9367e92110ba7fb232e89b9d950e491e5e8da5c7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407174"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Específicos de Microsoft**  
  
 Recupera el mensaje de cadena para HRESULT almacenado en el objeto `_com_error`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const TCHAR * ErrorMessage( ) const throw( );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el mensaje de cadena para HRESULT grabado dentro del `_com_error` objeto. Si el valor de HRESULT es un 16 bits asignado [wCode](../cpp/com-error-wcode.md), a continuación, un mensaje genérico "`IDispatch error #<wCode>`" se devuelve. Si no se encuentra ningún mensaje, se devuelve un mensaje genérico “`Unknown error #<hresult>`”. La cadena devuelta es Unicode o cadena multibyte, dependiendo del estado de la macro _UNICODE.  
  
## <a name="remarks"></a>Comentarios  
 Recupera el texto del mensaje del sistema adecuado para HRESULT grabado dentro del `_com_error` objeto. El texto del mensaje del sistema se obtiene mediante una llamada a Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) función. La API `FormatMessage` asigna la cadena devuelta, que se libera cuando se destruye el objeto `_com_error`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)