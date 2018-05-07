---
title: Error del compilador C2893 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db3b71a05ece6b79672d47699dc68e0eb5bb1f60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2893"></a>Error del compilador C2893
No se pudo especializar la plantilla de función 'nombre de plantilla'  
  
 El compilador no pudo especializar una plantilla de función. Puede haber varias causas para este error.  
  
 En general, la manera de solucionar el error 2893 es revisar la firma de la función y asegúrese de que puede crear instancias de cada tipo.  
  
## <a name="example"></a>Ejemplo  
 2893 se produce porque `f`del parámetro de plantilla `T` se deduce como `std::map<int,int>`, pero `std::map<int,int>` no tiene ningún miembro `data_type` (`T::data_type` no se pueden crear instancias con `T = std::map<int,int>`.). El ejemplo siguiente genera 2893.  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```