---
title: "odl | Microsoft Docs"
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
  - "vc-attr.odl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "odl attribute"
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# odl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Identifica una interfaz como una interfaz \(ODL\) del Lenguaje de descripción de objetos.  El compilador MIDL no requiere el atributo de **odl** ; sólo se reconoce para la compatibilidad con más antiguos archivos de .odl.  
  
## Sintaxis  
  
```  
  
[odl]  
  
```  
  
## Comentarios  
 el atributo de **odl** C\+\+ tiene la misma funcionalidad que el atributo de [odl](http://msdn.microsoft.com/library/windows/desktop/aa367126) MIDL.  
  
## Ejemplo  
  
```  
// cpp_attr_ref_odl.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLIb")];  
  
[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyInterface  
{  
   HRESULT x();  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
class cmyClass : public IMyInterface  
{  
public:  
   HRESULT x(){}  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)