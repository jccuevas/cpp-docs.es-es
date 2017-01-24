---
title: "_bstr_t::copy | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t::copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BSTR (objeto), copy"
  - "Copy (método)"
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::copy
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Crea una copia del objeto `BSTR` encapsulado.  
  
## Sintaxis  
  
```  
  
      BSTR copy(  
  bool fCopy = true  
) const;  
```  
  
#### Parámetros  
 `fCopy`  
 Si es **true**, **copy** devuelve una copia del objeto `BSTR` contenido; de lo contrario, **copy** devuelve el objeto BSTR real.  
  
## Comentarios  
 Devuelve una copia recién asignada del objeto `BSTR` encapsulado.  
  
## Ejemplo  
  
```  
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)