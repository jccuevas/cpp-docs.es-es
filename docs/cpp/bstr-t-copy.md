---
title: _bstr_t::Copy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d23f204e7e8a545fbee7ab516495ed711d7984a9
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944637"
---
# <a name="bstrtcopy"></a>_bstr_t::copy
**Específicos de Microsoft**  
  
 Crea una copia del objeto `BSTR` encapsulado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
BSTR copy( bool fCopy = true ) const;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *fCopy*  
 Si es TRUE, `copy` devuelve una copia de los contenidos `BSTR`en caso contrario, `copy` devuelve el objeto BSTR real.  
  
## <a name="remarks"></a>Comentarios  
 Devuelve una copia recién asignada del objeto `BSTR` encapsulado.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)