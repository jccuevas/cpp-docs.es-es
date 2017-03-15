---
title: "uuid (C++ Attributes) | Microsoft Docs"
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
  - "vc-attr.uuid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uuid attribute"
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uuid (C++ Attributes)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el identificador único para una clase o interfaz.  
  
## Sintaxis  
  
```  
  
      [ uuid(  
   "uuid"  
) ]  
```  
  
#### Parámetros  
 *uuid*  
 128 Bits, identificador único.  
  
## Comentarios  
 Si la definición de una interfaz o clase no especifica el atributo de `uuid` C\+\+, el compilador de Visual C\+\+ proporcionará uno.  Cuando se especifica `uuid`, debe incluir las comillas.  
  
 Si no especifica `uuid`, el compilador generará mismo GUID para interfaces o clases con el mismo nombre en distintos proyectos de atributo en un equipo.  
  
 Puede utilizar Uuidgen.exe o Guidgen.exe para ser id. únicos.  \(Para ejecutar cualquiera de estas herramientas, haga clic **Iniciar** y haga clic en **Ejecutar** en el menú.  Escriba el nombre de la herramienta necesaria.\)  
  
 Cuando se utiliza en un proyecto que tampoco utilice ATL, especificar el atributo de `uuid` es lo mismo que especificar el modificador \_\_declspec de [uuid](../cpp/uuid-cpp.md) .  Para recuperar `uuid` de una clase, puede utilizar [\_\_uuidof](../cpp/uuidof-operator.md)  
  
## Ejemplo  
 Vea el ejemplo de [enlazable](../windows/bindable.md) para un ejemplo de uso de `uuid`.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`, `interface`, **union**, `enum`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)