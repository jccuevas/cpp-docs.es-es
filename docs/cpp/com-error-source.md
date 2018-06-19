---
title: _com_error::Source | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Source
dev_langs:
- C++
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a33834df20606e8380e6a328a41435522185ac70
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412350"
---
# <a name="comerrorsource"></a>_com_error::Source
**Específicos de Microsoft**  
  
 Llamadas **IErrorInfo:: getSource** función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de **IErrorInfo:: getSource** para el **IErrorInfo** objeto registrado dentro del `_com_error` objeto. El BSTR resultante se encapsula en un objeto `_bstr_t`. Si no hay ningún **IErrorInfo** está registrado, devuelve una instancia vacía `_bstr_t`.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier error al llamar a la **IErrorInfo:: getSource** método se pasa por alto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)