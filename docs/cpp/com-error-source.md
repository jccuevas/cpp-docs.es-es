---
title: _com_error::Source | Microsoft Docs
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
ms.openlocfilehash: f722d1c4e8fc3d534403c2d18713e64dc2069011
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404904"
---
# <a name="comerrorsource"></a>_com_error::Source
**Específicos de Microsoft**  
  
 Llama a la función `IErrorInfo::GetSource`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_bstr_t Source() const;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de `IErrorInfo::GetSource` para el `IErrorInfo` objeto grabado dentro del `_com_error` objeto. El `BSTR` resultante se encapsula en un objeto `_bstr_t`. Si no hay ningún `IErrorInfo` está registrado, devuelve un valor vacío `_bstr_t`.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier error durante la llamada a la `IErrorInfo::GetSource` se omite el método.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_error (Clase)](../cpp/com-error-class.md)