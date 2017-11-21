---
title: Funciones &lt;istream&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da4b05286c56bf809914b142a254a311f8655ce9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ltistreamgt-functions"></a>Funciones &lt;istream&gt;
|||  
|-|-|  
|[swap](#istream_swap)|[ws](#ws)|  
  
##  <a name="istream_swap"></a>  swap  
 Intercambia los elementos de dos objetos stream.  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_istream<Elem, Tr>& left,  
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>  
void swap(
    basic_iostream<Elem, Tr>& left,  
    basic_iostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Flujo.  
  
 `right`  
 Flujo.  
  
##  <a name="ws"></a>  ws  
 Omite los espacios en blanco en el flujo.  
  
```  
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Istr`  
 Flujo.  
  
### <a name="return-value"></a>Valor devuelto  
 La secuencia.  
  
### <a name="remarks"></a>Comentarios  
 El manipulador extrae y descarta todos los elementos `ch` para los que [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **Elem**> >( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **ctype**\< **Elem**>:: **space**, **ch**) sea true.  
  
 La función llama a [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) si encuentra el final del archivo al extraer elementos. Devuelve `_Istr`.  
  
### <a name="example"></a>Ejemplo  
  Vea [operator>>](../standard-library/istream-operators.md#op_gt_gt) para obtener un ejemplo que usa `ws`.  
  
## <a name="see-also"></a>Vea también  
 [\<istream>](../standard-library/istream.md)

