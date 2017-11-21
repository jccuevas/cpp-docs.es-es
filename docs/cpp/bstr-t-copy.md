---
title: _bstr_t::Copy | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::copy
dev_langs: C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5c7a3bb2997bbec1c0e402c14985353dcf0bc768
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="bstrtcopy"></a>_bstr_t::copy
**Específicos de Microsoft**  
  
 Crea una copia del objeto `BSTR` encapsulado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      BSTR copy(  
  bool fCopy = true  
) const;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fCopy`  
 Si **true**, **copia** devuelve una copia del contenido `BSTR`, en caso contrario, **copia** devuelve el objeto BSTR real.  
  
## <a name="remarks"></a>Comentarios  
 Devuelve una copia recién asignada del objeto `BSTR` encapsulado.  
  
## <a name="example"></a>Ejemplo  
  
```  
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)