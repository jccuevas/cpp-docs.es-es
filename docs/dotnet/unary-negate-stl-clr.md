---
title: unary_negate (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::unary_negate
dev_langs:
- C++
helpviewer_keywords:
- unary_negate function [STL/CLR]
ms.assetid: 83bbdd86-199c-4451-9f70-72f9ade2264a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 60e7a38ede07a3cf3b1c21b1c5fe26e9f588f2f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="unarynegate-stlclr"></a>unary_negate (STL/CLR)
La clase de plantilla describe un functor que, cuando se llama, devuelve la operación lógica no de su almacenado functor de un argumento. Se usa especificar un objeto de función en cuanto a su functor almacenado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parámetros  
 Fun  
 El tipo del functor almacenado.  
  
## <a name="member-functions"></a>Funciones miembro  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|argument_type|El tipo del argumento functor.|  
|delegate_type|El tipo de delegado genérico.|  
|result_type|El tipo del resultado functor.|  
  
|Miembro|Descripción|  
|------------|-----------------|  
|unary_negate|Construye el functor.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|operator()|Calcula la función deseada.|  
|delegate_type ^|Convierte el functor a un delegado.|  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un functor de un argumento que almacena otro functor de un argumento. Define el operador de miembro `operator()` que, cuando se llama al objeto como una función, devuelve la operación lógica no del functor almacenado llamado con el argumento.  
  
 También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_unary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
1 0  
1 0  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/funcional >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [not1 (STL/CLR)](../dotnet/not1-stl-clr.md)