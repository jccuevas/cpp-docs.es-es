---
title: funcional (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/functional>
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 38bfbe025c92aa54956a165367b367cecc6160b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112841"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)
Incluya el encabezado STL/CLR `<cliext/functional>` para definir el un número de funciones y los delegados de plantilla relacionadas y clases de plantilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <functional>  
```  
  
## <a name="declarations"></a>Declaraciones  
  
|delegado|Descripción|  
|--------------|-----------------|  
|[binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)|Delegado de dos argumentos.|  
|[binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)|Delegado de dos argumentos devuelve `void`.|  
|[unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)|Delegado de un argumento.|  
|[unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)|Delegado de un argumento devuelve `void`.|  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)|Functor para negar un functor de dos argumentos.|  
|[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)|Functor para enlazar el primer argumento a un functor de dos argumentos.|  
|[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)|Functor para enlazar el segundo argumento a un functor de dos argumentos.|  
|[divides (STL/CLR)](../dotnet/divides-stl-clr.md)|Dividir functor.|  
|[equal_to (STL/CLR)](../dotnet/equal-to-stl-clr.md)|Functor de comparación igual.|  
|[greater (STL/CLR)](../dotnet/greater-stl-clr.md)|Functor de comparación mayor.|  
|[greater_equal (STL/CLR)](../dotnet/greater-equal-stl-clr.md)|Functor de comparación mayor o igual que.|  
|[less (STL/CLR)](../dotnet/less-stl-clr.md)|Menos functor de comparación.|  
|[less_equal (STL/CLR)](../dotnet/less-equal-stl-clr.md)|Functor de comparación menor o igual que.|  
|[logical_and (STL/CLR)](../dotnet/logical-and-stl-clr.md)|Functor AND lógico.|  
|[logical_not (STL/CLR)](../dotnet/logical-not-stl-clr.md)|Lógico no functor.|  
|[logical_or (STL/CLR)](../dotnet/logical-or-stl-clr.md)|Functor de OR lógico.|  
|[minus (STL/CLR)](../dotnet/minus-stl-clr.md)|Restar functor.|  
|[modulus (STL/CLR)](../dotnet/modulus-stl-clr.md)|Functor de módulo.|  
|[multiplies (STL/CLR)](../dotnet/multiplies-stl-clr.md)|Multiplicar functor.|  
|[negate (STL/CLR)](../dotnet/negate-stl-clr.md)|Functor para devolver su argumento negada.|  
|[not_equal_to (STL/CLR)](../dotnet/not-equal-to-stl-clr.md)|Functor de comparación no es igual.|  
|[plus (STL/CLR)](../dotnet/plus-stl-clr.md)|Agregar functor.|  
|[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)|Functor para negar un functor de un argumento.|  
  
|Función|Descripción|  
|--------------|-----------------|  
|[bind1st (STL/CLR)](../dotnet/bind1st-stl-clr.md)|Genera un binder1st por un functor y un argumento.|  
|[bind2nd (STL/CLR)](../dotnet/bind2nd-stl-clr.md)|Genera un binder2nd por un functor y un argumento.|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|Genera un unary_negate para un functor.|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|Genera un binary_negate para un functor.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/funcional >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)