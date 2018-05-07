---
title: range_adapter (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- range_adapter class [STL/CLR]
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a5b8a02856d7739867e3cf9f76f866a1e84efca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="rangeadapter-stlclr"></a>range_adapter (STL/CLR)
Una clase de plantilla que contenga un par de iteradores que se usan para implementar varias interfaces de la biblioteca de clases Base (BCL). Utilice la range_adapter para manipular un intervalo STL/CLR como si fuera una colección de BCL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parámetros  
 ITER  
 El tipo asociado con los iteradores ajustados.  
  
## <a name="members"></a>Miembros  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](../dotnet/range-adapter-range-adapter-stl-clr.md)|Construye un objeto de adaptador.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](../dotnet/range-adapter-operator-assign-stl-clr.md)|Reemplaza el par de iterador almacenado.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|Recorre en iteración los elementos de la colección.|  
|<xref:System.Collections.ICollection>|Mantiene un grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Recorre en iteración los elementos con tipo en la colección...|  
|<xref:System.Collections.Generic.ICollection%601>|Mantiene un grupo de elementos con tipo.|  
  
## <a name="remarks"></a>Comentarios  
 El range_adapter almacena un par de iteradores, que a su vez delimitar una secuencia de elementos. El objeto implementa cuatro interfaces BCL que le permiten recorrer en iteración los elementos en orden. Utilice esta clase de plantilla para manipular los intervalos STL/CLR como contenedores BCL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/adaptador >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)