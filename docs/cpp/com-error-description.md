---
title: _com_error::Description | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3ed306a8eba4e76c2eefc738b617117188e85c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comerrordescription"></a>_com_error::Description
**Específicos de Microsoft**  
  
 Llamadas **IErrorInfo:: GetDescription** función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
_bstr_t Description( ) const;  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de **IErrorInfo:: GetDescription** para el **IErrorInfo** objeto registrado dentro del `_com_error` objeto. El `BSTR` resultante se encapsula en un objeto `_bstr_t`. Si no hay ningún **IErrorInfo** está registrado, devuelve una instancia vacía `_bstr_t`.  
  
## <a name="remarks"></a>Comentarios  
 Llamadas el **IErrorInfo:: GetDescription** función y recupera **IErrorInfo** registrado dentro del `_com_error` objeto. Cualquier error al llamar a la **IErrorInfo:: GetDescription** método se pasa por alto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)