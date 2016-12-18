---
title: "ms_union | Microsoft Docs"
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
  - "vc-attr.ms_union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ms_union attribute"
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ms_union
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

controla la alineación de la representación de datos de la red de uniones nonencapsulated.  
  
## Sintaxis  
  
```  
  
[ms_union]  
  
```  
  
## Comentarios  
 el atributo de **ms\_union** C\+\+ tiene la misma funcionalidad que el atributo de [ms\_union](http://msdn.microsoft.com/library/windows/desktop/aa367100) MIDL.  
  
## Ejemplo  
 el código siguiente muestra la posición de **ms\_union**:  
  
```  
// cpp_attr_ref_ms_union.cpp  
// compile with: /LD  
#include <unknwn.h>  
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl {  
   HRESULT DisplayString([in, string] char * p1);  
};  
  
[export, switch_type(short)] union _WILLIE_UNION_TYPE  {  
   [case(24)]  
      float fMays;  
   [case(25)]  
      double dMcCovey;  
   [default]  
      int x;  
 };  
  
[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;  
  
[module(name="ATLFIRELib")];  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|uniones de Nonencapsulated|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|**dispinterface**|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)