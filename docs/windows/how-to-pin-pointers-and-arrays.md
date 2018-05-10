---
title: 'Cómo: anclar punteros y matrices | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b1cea9b1c7c6738c33f00e984aa8212d611b4aec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-pin-pointers-and-arrays"></a>Cómo: Anclar punteros y matrices
Anclar un subobjeto definido en un objeto administrado tiene el efecto de todo el objeto de anclaje.  Por ejemplo, si se ancla un elemento de una matriz, también se ancla la matriz entera. No hay ninguna extensión del lenguaje para declarar una matriz anclada. Para anclar la matriz, declare un puntero anclado para su tipo de elemento y el pin uno de sus elementos.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
  
```  
// pin_ptr_array.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
int main() {  
   array<Byte>^ arr = gcnew array<Byte>(4);  
   arr[0] = 'C';  
   arr[1] = '+';  
   arr[2] = '+';  
   arr[3] = '\0';  
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned  
   unsigned char * cp = p;  
  
   printf_s("%s\n", cp); // bytes pointed at by cp  
                         // will not move during call  
}  
```  
  
### <a name="output"></a>Salida  
  
```  
++  
```  
  
## <a name="see-also"></a>Vea también  
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)