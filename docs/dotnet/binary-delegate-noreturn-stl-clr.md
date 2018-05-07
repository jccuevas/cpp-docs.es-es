---
title: binary_delegate_noreturn (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::binary_delegate_noreturn
dev_langs:
- C++
helpviewer_keywords:
- binary_delegate_noreturn function [STL/CLR]
ms.assetid: 055c7e9d-e5c3-48fe-9327-3f6316e8a51e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 31ea9d7ab2c8421caf21846005b6092bf29eee8a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="binarydelegatenoreturn-stlclr"></a>binary_delegate_noreturn (STL/CLR)
La clase genereic describe un delegado de dos argumentos que devuelve `void`. Se usa especificar un delegado en cuanto a su argumento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
generic<typename Arg1,  
    typename Arg2>  
    delegate void binary_delegate(Arg1, Arg2);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Arg1  
 El tipo del primer argumento.  
  
 Arg2  
 El tipo del segundo argumento.  
  
## <a name="remarks"></a>Comentarios  
 El delegado genereic describe una función de dos argumentos que devuelve `void`.  
  
 Tenga en cuenta que para:  
  
 `binary_delegate_noreturn<int, int> Fun1;`  
  
 `binary_delegate_noreturn<int, int> Fun2;`  
  
 los tipos de `Fun1` y `Fun2` son sinónimos, mientras que para:  
  
 `delegate void Fun1(int, int);`  
  
 `delegate void Fun2(int, int);`  
  
 no son del mismo tipo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_binary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void key_compare(wchar_t left, wchar_t right)   
    {   
    System::Console::WriteLine("compare({0}, {1}) = {2}",   
        left, right, left < right);   
    }   
  
typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    kcomp(L'a', L'a');   
    kcomp(L'a', L'b');   
    kcomp(L'b', L'a');   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(a, a) = False  
compare(a, b) = True  
compare(b, a) = False  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/funcional >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)   
 [unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)   
 [unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)