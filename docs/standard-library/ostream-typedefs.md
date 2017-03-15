---
title: Definiciones de tipo &lt;ostream&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 310954b0965be071c288f09de058e3cebe3ce27d
ms.lasthandoff: 02/24/2017

---
# <a name="ltostreamgt-typedefs"></a>Definiciones de tipo &lt;ostream&gt;
|||  
|-|-|  
|[ostream](#ostream)|[wostream](#wostream)|  
  
##  <a name="a-nameostreama--ostream"></a><a name="ostream"></a> ostream  
 Crea un tipo de basic_ostream que está especializado en `char` y `char_traits` especializado en `char`.  
  
```
typedef basic_ostream<char, char_traits<char>> ostream;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), especializada en elementos de tipo `char` con rasgos de caracteres predeterminados.  
  
##  <a name="a-namewostreama--wostream"></a><a name="wostream"></a> wostream  
 Crea un tipo de basic_ostream que está especializado en `wchar_t` y `char_traits` especializado en `wchar_t`.  
  
```
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), especializada en elementos de tipo `wchar_t` con rasgos de caracteres predeterminados.  
  
## <a name="see-also"></a>Vea también  
 [\<ostream>](../standard-library/ostream.md)




