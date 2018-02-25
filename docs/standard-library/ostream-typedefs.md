---
title: Definiciones de tipo &lt;ostream&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: c9ab11cf6436888605a07c91051bf27c45e10fcf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ltostreamgt-typedefs"></a>Definiciones de tipo &lt;ostream&gt;
|||  
|-|-|  
|[ostream](#ostream)|[wostream](#wostream)|  
  
##  <a name="ostream"></a> ostream  
 Crea un tipo de basic_ostream que está especializado en `char` y `char_traits` especializado en `char`.  
  
```
typedef basic_ostream<char, char_traits<char>> ostream;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), especializada en elementos de tipo `char` con rasgos de caracteres predeterminados.  
  
##  <a name="wostream"></a> wostream  
 Crea un tipo de basic_ostream que está especializado en `wchar_t` y `char_traits` especializado en `wchar_t`.  
  
```
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), especializada en elementos de tipo `wchar_t` con rasgos de caracteres predeterminados.  
  
## <a name="see-also"></a>Vea también  
 [\<ostream>](../standard-library/ostream.md)



