---
title: "registration_script | Microsoft Docs"
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
  - "vc-attr.registration_script"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "registration_script attribute"
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# registration_script
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ejecuta el script personalizado especificado del registro.  
  
## Sintaxis  
  
```  
  
      [ registration_script(   
   script   
) ]  
```  
  
#### Parámetros  
 *script*  
 La ruta de acceso completa a un archivo de script de registro \(.rgs\).  Un valor de **cualquier**, como `script = "none"`, indica que la coclase no tienen ningún requisito de registro.  
  
## Comentarios  
 El atributo de **registration\_script** C\+\+ ejecuta el script personalizado de registro especificado por **script**.  Si no se especifica este atributo, un archivo standard .rgs \(que contiene información para registrar el componente\) se utiliza.  Para obtener más información sobre los archivos .rgs, vea [El componente de registro ATL \(registro\)](../atl/atl-registry-component-registrar.md).  
  
 Este atributo requiere que [CoClass](../windows/coclass.md), [ProgID](../Topic/progid.md), o el atributo de [vi\_progid](../windows/vi-progid.md) \(u otro atributo que implica una de estas\) también se aplican al mismo elemento.  
  
## Ejemplo  
 El código siguiente especifica que el componente tiene un script de registro denominado cpp\_attr\_ref\_registration\_script.rgs.  
  
```  
// cpp_attr_ref_registration_script.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="REG")];  
  
[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]  
__interface IFace {};  
  
// requires "cpp_attr_ref_registration_script.rgs"  
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist  
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),  
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]  
class CMyClass:public IFace {};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|Uno o más de los siguientes: **CoClass**, **ProgID**, o **vi\_progid**.|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [COM Attributes](../Topic/COM%20Attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [rdx](../windows/rdx.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)