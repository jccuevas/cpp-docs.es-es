---
title: Error de compilador Error C2728 | Documentos de Microsoft
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0f83665f1f2b388ac751dd4fd4aec2f75e8651a3
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2728"></a>Error C2728 de Error del compilador
'type': una matriz nativa no puede contener este tipo  
  
 Se usó la sintaxis de creación de matrices para crear una matriz de objetos administrados u objetos de WinRT. No se puede crear una matriz de objetos administrados u objetos de WinRT mediante la sintaxis de matriz nativa.  
  
 Para obtener más información, vea [Matriz](../../windows/arrays-cpp-component-extensions.md).  
  
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

