---
title: Pair::operator = (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::pair::operator=
dev_langs: C++
helpviewer_keywords: operator= member [STL/CLR]
ms.assetid: b6228037-914e-4efa-8491-65dbb0e93f61
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aa722f53c9ad76c32486d493db6d37e70ce12879
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="pairoperator-stlclr"></a>pair::operator= (STL/CLR)
Reemplaza el par de valores almacenado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Par va a copiar.  
  
## <a name="remarks"></a>Comentarios  
 Las copias de operador de miembro `right` en el objeto, a continuación, devuelve `*this`. Úselo para reemplazar el par de valores almacenado por una copia del par de valores almacenado `right`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_pair_operator_as.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
// assign to a new pair   
    cliext::pair<wchar_t, int> c2;   
    c2 = c1;   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 3]  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/utilidad >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [pair (STL/CLR)](../dotnet/pair-stl-clr.md)