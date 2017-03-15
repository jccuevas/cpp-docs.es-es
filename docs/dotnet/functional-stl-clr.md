---
title: "functional (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "<cliext/functional>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/functional> (encabezado) [STL/CLR]"
  - "<functional> (encabezado) [STL/CLR]"
  - "functional (funciones) [STL/CLR]"
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# functional (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado `<cliext/functional>` de STL\/CLR para definir varias clases de plantilla y delegados relacionados y funciones de la plantilla.  
  
## Sintaxis  
  
```  
#include <functional>  
```  
  
## Declaraciones  
  
|Delegate|Descripción|  
|--------------|-----------------|  
|[binary\_delegate](../dotnet/binary-delegate-stl-clr.md)|Delegado de Dos\- argumento.|  
|[binary\_delegate\_noreturn](../dotnet/binary-delegate-noreturn-stl-clr.md)|Delegado de Dos\- argumento que devuelve `void`.|  
|[unary\_delegate](../dotnet/unary-delegate-stl-clr.md)|Delegado de Uno\- argumento.|  
|[unary\_delegate\_noreturn](../dotnet/unary-delegate-noreturn-stl-clr.md)|Delegado de Uno\- argumento que devuelve `void`.|  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[binary\_negate](../dotnet/binary-negate-stl-clr.md)|Functor para invalidar un functor de dos\- argumento.|  
|[binder1st](../dotnet/binder1st-stl-clr.md)|Functor para enlazar el primer argumento un functor de dos\- argumento.|  
|[binder2nd](../dotnet/binder2nd-stl-clr.md)|Functor para enlazar el segundo argumento un functor de dos\- argumento.|  
|[divides](../dotnet/divides-stl-clr.md)|Functor de división.|  
|[equal\_to](../dotnet/equal-to-stl-clr.md)|Functor igual de comparación.|  
|[greater](../dotnet/greater-stl-clr.md)|Mayor functor de comparación.|  
|[greater\_equal](../dotnet/greater-equal-stl-clr.md)|Functor mayor o igual de comparación.|  
|[less](../dotnet/less-stl-clr.md)|Menos functor de comparación.|  
|[less\_equal](../dotnet/less-equal-stl-clr.md)|Menos o functor igual de comparación.|  
|[logical\_and](../dotnet/logical-and-stl-clr.md)|Functor lógico AND.|  
|[logical\_not](../dotnet/logical-not-stl-clr.md)|Functor de la negación lógica.|  
|[logical\_or](../dotnet/logical-or-stl-clr.md)|Functor OR lógica.|  
|[minus](../dotnet/minus-stl-clr.md)|Restar el functor.|  
|[módulo](../dotnet/modulus-stl-clr.md)|Functor de módulo.|  
|[multiplies](../dotnet/multiplies-stl-clr.md)|Multiplique el functor.|  
|[negate](../dotnet/negate-stl-clr.md)|Functor devolver su argumento negado.|  
|[not\_equal\_to](../dotnet/not-equal-to-stl-clr.md)|Functor no igual de comparación.|  
|[plus](../dotnet/plus-stl-clr.md)|Agregue el functor.|  
|[unary\_negate](../dotnet/unary-negate-stl-clr.md)|Functor para invalidar un functor de uno\- argumento.|  
  
|Función|Descripción|  
|-------------|-----------------|  
|[bind1st](../dotnet/bind1st-stl-clr.md)|Genera un binder1st para un argumento y un functor.|  
|[bind2nd](../dotnet/bind2nd-stl-clr.md)|Genera un binder2nd para un argumento y un functor.|  
|[not1](../dotnet/not1-stl-clr.md)|Genera un unary\_negate para un functor.|  
|[not1](../dotnet/not1-stl-clr.md)|Genera un binary\_negate para un functor.|  
  
## Requisitos  
 cliext \<de**Encabezado:** \/funcional\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)