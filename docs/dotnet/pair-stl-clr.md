---
title: par (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair
dev_langs:
- C++
helpviewer_keywords:
- pair class [STL/CLR]
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2d05dceaa763f8d0e33ccc86e783f66447c48b76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160828"
---
# <a name="pair-stlclr"></a>pair (STL/CLR)
La clase de plantilla describe un objeto que contiene un par de valores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>Parámetros  
 Valor1  
 El tipo de valor incluido en primer lugar.  
  
 Value2  
 El tipo del segundo valor ajustada.  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](../dotnet/pair-first-type-stl-clr.md)|El tipo del primer valor ajustado.|  
|[pair::second_type (STL/CLR)](../dotnet/pair-second-type-stl-clr.md)|El tipo del segundo valor ajustado.|  
  
|Objeto de miembro|Descripción|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)|El primer valor almacenado.|  
|[pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)|El segundo valor almacenado.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](../dotnet/pair-pair-stl-clr.md)|Construye un objeto de par.|  
|[pair::swap (STL/CLR)](../dotnet/pair-swap-stl-clr.md)|Intercambia el contenido de dos pares.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](../dotnet/pair-operator-assign-stl-clr.md)|Reemplaza el par de valores almacenado.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto almacena un par de valores. Utilice esta clase de plantilla para combinar los dos valores en un único objeto. Tenga en cuenta que `cliext::pair` (que se describe aquí) almacena solo los tipos administrados; para almacenar un par de no administrado que utilice tipos `std::pair`, declarado en `<utility>`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/utilidad >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [make_pair (STL/CLR)](../dotnet/make-pair-stl-clr.md)