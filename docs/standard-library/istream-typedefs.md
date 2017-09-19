---
title: Definiciones de tipo &lt;istream&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e3607735f989b61f373eb689b8fe3b2dee656f7b
ms.lasthandoff: 02/24/2017

---
# <a name="ltistreamgt-typedefs"></a>Definiciones de tipo &lt;istream&gt;
||||  
|-|-|-|  
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|  
|[wistream](#wistream)|  
  
##  <a name="iostream"></a>  iostream  
 Tipo `basic_iostream` especializado en `char`.  
  
```  
typedef basic_iostream<char, char_traits<char>> iostream;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es sinónimo de la clase de plantilla [basic_iostream](../standard-library/basic-iostream-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.  
  
##  <a name="istream"></a>  istream  
 Tipo `basic_istream` especializado en `char`.  
  
```  
typedef basic_istream<char, char_traits<char>> istream;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es sinónimo de la clase de plantilla [basic_istream](../standard-library/basic-istream-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.  
  
##  <a name="wiostream"></a>  wiostream  
 Tipo `basic_iostream` especializado en `wchar_t`.  
  
```  
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es sinónimo de la clase de plantilla [basic_iostream](../standard-library/basic-iostream-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.  
  
##  <a name="wistream"></a>  wistream  
 Tipo `basic_istream` especializado en `wchar_t`.  
  
```  
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es sinónimo de la clase de plantilla [basic_istream](../standard-library/basic-istream-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.  
  
## <a name="see-also"></a>Vea también  
 [\<istream>](../standard-library/istream.md)


