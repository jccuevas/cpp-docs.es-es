---
title: "restricted | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.restricted"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "restricted attribute"
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# restricted
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica que un miembro de módulo, interfaz, o de dispinterface no puede ser llamado arbitrariamente.  
  
## Sintaxis  
  
```  
  
      [ restricted(  
   interfaces  
) ]  
```  
  
#### Parámetros  
 `interfaces`  
 Una o más interfaces que no se puede llamar arbitrariamente en un objeto COM.  Este parámetro sólo es válido cuando se aplica a una clase.  
  
## Comentarios  
 el atributo de **Restringido** C\+\+ tiene la misma funcionalidad que el atributo de [Restringido](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL.  
  
## Ejemplo  
 el código siguiente muestra cómo utilizar el atributo de **Restringido** :  
  
```  
// cpp_attr_ref_restricted.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface b  
{  
};  
  
[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]  
class c : public a, public b  
{  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|método de interfaz, `interface`, **clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|**CoClass** \(cuando se aplica a **clase** o a `struct`\)|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)