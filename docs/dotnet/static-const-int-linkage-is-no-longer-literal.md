---
title: "Vinculación de miembros integrales Const estáticos ya No es Literal | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- literal attribute [C++]
- constants, declaring
- integral constant expressions
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8f34682fa780ef430d27104d3df9658f9e32ad39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>La vinculación de miembros integrales const estáticos ya no es literal
Declaración de un miembro de constante de una clase ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 Aunque `static const` todavía se admiten los miembros enteros, su atributo de vinculación ha cambiado. Su atributo de vinculación anterior ahora lo lleva un miembro entero literal. Por ejemplo, considere la siguiente clase de extensiones administradas:  
  
```  
public __gc class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 Esto genera los siguientes atributos CIL subyacentes para el campo (tenga en cuenta el atributo literal):  
  
```  
.field public static literal int32   
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Aunque esto aún se compila en la nueva sintaxis:  
  
```  
public ref class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 ya no se emite el atributo literal y, por tanto, no se visualiza como una constante en tiempo de ejecución de CLR:  
  
```  
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Para tener el mismo atributo literal entre lenguaje, la declaración debe cambiarse a recién admitidas `literal` miembro de datos, como se indica a continuación,  
  
```  
public ref class Constants {  
public:  
   literal int LOG_DEBUG = 4;  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de miembros en una clase o interfaz (C++ / CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [literal](../windows/literal-cpp-component-extensions.md)