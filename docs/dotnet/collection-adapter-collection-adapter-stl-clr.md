---
title: collection_adapter::collection_adapter (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
dev_langs:
- C++
helpviewer_keywords:
- collection_adapter member [STL/CLR]
ms.assetid: 7e2bb75b-d735-4135-9523-719683e06fe9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ddb802e372dfb10acdc6280622bf1ed59a422987
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108967"
---
# <a name="collectionadaptercollectionadapter-stlclr"></a>collection_adapter::collection_adapter (STL/CLR)
Construye un objeto de adaptador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>Parámetros  
 colección  
 Identificador BCL que va a contener.  
  
 right  
 Objeto que se va a copiar.  
  
## <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `collection_adapter();`  
  
 Inicializa el identificador almacenado con `nullptr`.  
  
 El constructor:  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 Inicializa el identificador almacenado con `right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 El constructor:  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 Inicializa el identificador almacenado con `right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 El constructor:  
  
 `collection_adapter(Coll^ collection);`  
  
 Inicializa el identificador almacenado con `collection`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
base() null = True  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/adaptador >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [collection_adapter::operator= (STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)