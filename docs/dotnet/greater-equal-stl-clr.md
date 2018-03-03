---
title: greater_equal (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::greater_equal
dev_langs:
- C++
helpviewer_keywords:
- greater_equal function [STL/CLR]
ms.assetid: 4d4d8301-72dd-4a06-a652-5237e1e72a88
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2d66689ff8b9cddb1ac2e88cb5e4c01f9f09b4ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="greaterequal-stlclr"></a>greater_equal (STL/CLR)
La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si el primer argumento es mayor o igual que la segunda. Se usa especificar un objeto de función en cuanto a su tipo de argumento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Arg>  
    ref class greater_equal  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater_equal();  
    greater_equal(greater_equal<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parámetros  
 Arg  
 El tipo de los argumentos.  
  
## <a name="member-functions"></a>Funciones miembro  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|delegate_type|El tipo de delegado genérico.|  
|first_argument_type|El tipo del primer argumento functor.|  
|result_type|El tipo del resultado functor.|  
|second_argument_type|El tipo del segundo argumento functor.|  
  
|Miembro|Descripción|  
|------------|-----------------|  
|greater_equal|Construye el functor.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|operator()|Calcula la función deseada.|  
|operador delegate_type ^|Convierte el functor a un delegado.|  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un functor de dos argumentos. Define el operador de miembro `operator()` que, cuando se llama al objeto como una función, devuelve true solo si el primer argumento es mayor o igual que la segunda.  
  
 También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_greater_equal.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::greater_equal<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
1 0  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/funcional >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [less (STL/CLR)](../dotnet/less-stl-clr.md)