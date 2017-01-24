---
title: "call_as | Microsoft Docs"
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
  - "vc-attr.call_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "call_as attribute"
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# call_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Permite a una función de [local](../windows/local-cpp.md) asignarlos a una función remota para cuando se llama a la función remota, invocar la función local.  
  
## Sintaxis  
  
```  
  
      [ call_as(  
   function  
) ]  
```  
  
#### Parámetros  
 *función*  
 La función local que desea llamar cuando se invoca una función remota.  
  
## Comentarios  
 el atributo de **call\_as** C\+\+ tiene la misma funcionalidad que el atributo de [call\_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) MIDL.  
  
## Ejemplo  
 El código siguiente muestra cómo puede utilizar **call\_as** asignar una función de uso no remoto \(**f1**\) a una función remota \(**Remf1**\):  
  
```  
// cpp_attr_ref_call_as.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMInterface {  
   [local] HRESULT f1 ( int i );  
   [call_as(f1)] HRESULT Remf1 ( int i );   
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [local](../windows/local-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)