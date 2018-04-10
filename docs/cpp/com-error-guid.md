---
title: _com_error::GUID | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1165f53027c5b8a116f97cd2660c7ca12c9e7302
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorguid"></a>_com_error::GUID
**Específicos de Microsoft**  
  
 Llamadas **IErrorInfo:: GetGuid** función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de **IErrorInfo:: GetGuid** para el **IErrorInfo** objeto registrado dentro del `_com_error` objeto. Si no hay ningún **IErrorInfo** se registra el objeto, devuelve `GUID_NULL`.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier error al llamar a la **IErrorInfo:: GetGuid** método se pasa por alto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)