---
title: C2728 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2728
dev_langs:
- C++
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
caps.latest.revision: 17
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 4e28f463dffeda0bc1b44da4d4e228771f59cc4c
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2728"></a>C2728 de Error del compilador
'type': una matriz nativa no puede contener este tipo  
  
 Se usó la sintaxis de creación de matrices para crear una matriz de objetos administrados u objetos de WinRT. No se puede crear una matriz de objetos administrados u objetos de WinRT mediante la sintaxis de matriz nativa.  
  
 Para obtener más información, consulte [matriz](../../windows/arrays-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera el error C2728 y muestra cómo corregirlo:  
  
```  
// C2728.cpp  
// compile with: /clr  
  
int main() {  
   int^ arr[5];   // C2728  
  
   // try the following line instead  
   array<int>^arr2;  
}  
```  

