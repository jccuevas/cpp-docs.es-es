---
title: "satype | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.satype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "satype attribute"
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# satype
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

especifica el tipo de datos de la estructura de **SAFEARRAY** .  
  
## Sintaxis  
  
```  
  
      [ satype(  
   data_type  
) ]  
```  
  
#### Parámetros  
 *data\_type*  
 El tipo de datos para la estructura de datos de **SAFEARRAY** que se pasa como parámetro a un método de interfaz.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Parámetro de interfaz, método de interfaz|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
## Comentarios  
 el atributo de **satype** C\+\+ especifica el tipo de datos de **SAFEARRAY**.  
  
> [!NOTE]
>  Un nivel de direccionamiento indirecto se quita del puntero de **SAFEARRAY** en el archivo generado .idl de cómo se declara en el archivo .cpp.  
  
## Ejemplo  
  
```  
// cpp_attr_ref_satype.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyModule")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A {  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## Vea también  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [id](../windows/id.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)