---
title: _bstr_t::Copy | Documentos de Microsoft
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
ms.openlocfilehash: c7337669cae68c088265d812585a44fadd6bcb76
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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