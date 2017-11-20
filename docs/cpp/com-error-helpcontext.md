---
title: _com_error::HelpContext | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::HelpContext
dev_langs: C++
helpviewer_keywords: HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7c350a2c8879ecf927974aa48650c59247716c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Específicos de Microsoft**  
  
 Llamadas **IErrorInfo:: GetHelpContext** función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de **IErrorInfo:: GetHelpContext** para el **IErrorInfo** objeto registrado dentro del `_com_error` objeto. Si no hay ningún **IErrorInfo** se registra el objeto, devuelve cero.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier error al llamar a la **IErrorInfo:: GetHelpContext** método se pasa por alto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)