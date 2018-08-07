---
title: 'Cómo: declarar punteros anclados y tipos de valor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57c6ed79f9ecb74533a7ffaf2861af8bee9e257a
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569760"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Cómo: Declarar punteros anclados y tipos de valor
Un tipo de valor puede ser implícitamente la conversión boxing. A continuación, puede declarar un puntero anclado para el objeto de tipo de valor propio y usar un **pin_ptr** al tipo de valor con conversión boxing.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
  
```cpp  
// pin_ptr_value.cpp  
// compile with: /clr  
value struct V {  
   int i;  
};  
  
int main() {  
   V ^ v = gcnew V;   // imnplicit boxing  
   v->i=8;  
   System::Console::WriteLine(v->i);  
   pin_ptr<V> mv = &*v;  
   mv->i = 7;  
   System::Console::WriteLine(v->i);  
   System::Console::WriteLine(mv->i);  
}  
```  
  
### <a name="output"></a>Salida  
  
```Output  
8  
7  
7  
```  
  
## <a name="see-also"></a>Vea también  
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)