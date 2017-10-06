---
title: _bstr_t::Copy | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 25167305ae817ebd9d979c0145934996bbbfcddc
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
