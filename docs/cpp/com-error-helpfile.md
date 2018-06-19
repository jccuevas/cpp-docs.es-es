---
title: _com_error::HelpFile | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1f02238d228b5de4302812bacf4f9ad5cf1300c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409792"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile
**Específicos de Microsoft**  
  
 Llamadas **IErrorInfo:: GetHelpFile** función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de **IErrorInfo:: GetHelpFile** para el **IErrorInfo** objeto registrado dentro del `_com_error` objeto. El BSTR resultante se encapsula en un objeto `_bstr_t`. Si no hay ningún **IErrorInfo** está registrado, devuelve una instancia vacía `_bstr_t`.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier error al llamar a la **IErrorInfo:: GetHelpFile** método se pasa por alto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)