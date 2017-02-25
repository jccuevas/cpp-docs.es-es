---
title: "Interpretaci&#243;n del operador de sub&#237;ndice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], subíndices"
  - "interpretación de operadores de subíndice"
  - "operadores [C++], interpretación de subíndice"
  - "operador de subíndice, Interpretación de"
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Interpretaci&#243;n del operador de sub&#237;ndice
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al igual que otros operadores, el operador de subíndice \(**\[ \]**\) lo puede volver a definir el usuario.  El comportamiento predeterminado del operador de subíndice, si no está sobrecargado, consiste en combinar el nombre de la matriz y el subíndice usando el método siguiente:  
  
 \*\(\(*array\-name*\) \+ \(*subscript*\)\)  
  
 Como en toda suma que implica tipos de puntero, el ajuste de escala se realiza automáticamente para que se produzca el ajuste correspondiente al tamaño del tipo.  Por lo tanto, el valor resultante no tiene bytes *subscript* desde el origen de *array\-name*; en su lugar, es el elemento *subscript*n de la matriz. \(Para obtener más información sobre esta conversión, vea [Operadores de suma](../cpp/additive-operators-plus-and.md).\)  
  
 De igual forma, para las matrices multidimensionales, la dirección se deriva usando el método siguiente:  
  
 **\(\(**   
 ***array\-name* \) \+ \(**   
 ***subscript* 1**  *max*2 *\* max*3*...max*n\)               **\+** *subscript*2 *\* max*3*...max*n\)                    . . .  *\+* *subscript*n\)\)  
  
## Vea también  
 [Matrices](../cpp/arrays-cpp.md)