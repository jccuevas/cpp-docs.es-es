---
title: "inner_product (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::inner_product"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inner_product (función) [STL/CLR]"
ms.assetid: 97d7a507-7494-4216-aedf-0546ed0edb3f
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# inner_product (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula la suma del producto mejor elemento de dos intervalos y la agrega a un valor inicial especificado o calcula el resultado de un procedimiento general donde la suma y operaciones binarias del producto se reemplazan con otras operaciones binarias especificadas.  
  
## Sintaxis  
  
```  
template<class _InIt1, class _InIt2, class _Ty> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val);  
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,  
       class _Fn22> inline  
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función numérica `inner_product`STL.  Para obtener más información, vea [inner\_product](../Topic/inner_product.md).  
  
## Requisitos  
 cliext \<de**Encabezado:** \/numérico\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [numeric](../dotnet/numeric-stl-clr.md)