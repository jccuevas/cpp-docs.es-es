---
title: "readonly (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.readonly"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atributo de solo lectura"
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# readonly (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Prohíbe la asignación a un miembro de datos.  
  
## Sintaxis  
  
```  
  
[readonly]  
  
```  
  
## Comentarios  
 El atributo de C\+\+ **readonly** tiene la misma funcionalidad que el atributo MIDL [readonly](http://msdn.microsoft.com/library/windows/desktop/aa367152).  
  
 Si quiere prohibir la modificación de un parámetro de método, use el atributo [in](../Topic/in%20\(C++\).md).  
  
## Ejemplo  
 En el código siguiente se muestra el uso del atributo **readonly**:  
  
```  
// cpp_attr_ref_readonly.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]  
__interface IFireTabCtrl  
{  
   [readonly, id(1)] int i();  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Data Member Attributes](../windows/data-member-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)