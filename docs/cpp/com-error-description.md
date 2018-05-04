---
title: _com_error::Description | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7df1fb3a8ca600b888e5d6f2c51fc44fda17dd27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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