---
title: logical_not (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::logical_not
dev_langs:
- C++
helpviewer_keywords:
- logical_not function [STL/CLR]
ms.assetid: 32a2c6e2-1c58-41ac-8827-f3ee5adfe81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4048c642a1c562237bccba8fa3e5fd5429bba4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="logicalnot-stlclr"></a>logical_not (STL/CLR)
La clase de plantilla describe un functor que, cuando se llama, devuelve true solo si su argumento prueba como false. Se usa especificar un objeto de función en cuanto a su tipo de argumento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Arg>  
    ref class logical_not  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    logical_not();  
    logical_not(logical_not<Arg> %right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parámetros  
 Arg  
 El tipo de los argumentos.  
  
## <a name="member-functions"></a>Funciones miembro  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|argument_type|El tipo del argumento functor.|  
|delegate_type|El tipo de delegado genérico.|  
|result_type|El tipo del resultado functor.|  
  
|Miembro|Descripción|  
|------------|-----------------|  
|logical_not|Construye el functor.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|operator()|Calcula la función deseada.|  
|operador delegate_type ^|Convierte el functor a un delegado.|  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un functor de un argumento. Define el operador de miembro `operator()` que, cuando se llama al objeto como una función, que devuelve true solo si su argumento pruebas como false.  
  
 También puede pasar el objeto como un argumento de función cuyo tipo es `delegate_type^` y se convertirán correctamente.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_logical_not.cpp   
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
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::logical_not<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
0 1  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/funcional >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [negate (STL/CLR)](../dotnet/negate-stl-clr.md)