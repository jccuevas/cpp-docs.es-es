---
title: "dispinterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.dispinterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dispinterface (atributo)"
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# dispinterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Coloca una interfaz en el archivo .idl como interfaz de envío.  
  
## Sintaxis  
  
```  
  
[dispinterface]  
  
```  
  
## Comentarios  
 Cuando el atributo de C\+\+ **dispinterface** precede a una interfaz, hace que esta se coloque dentro del bloque de biblioteca del archivo .idl generado.  
  
 A menos que especifique una clase base, se derivará una interfaz de envío de `IDispatch`. Debe especificar un [id](../windows/id.md) para los miembros de una interfaz de envío.  
  
 El ejemplo de uso de [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) en la documentación de MIDL:  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 no es válido para el atributo **dispinterface**.  
  
## Ejemplo  
 Consulte el ejemplo de [bindable](../windows/bindable.md) para ver un ejemplo de cómo usar **dispinterface**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`interface`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|**dual**, **object**, **oleautomation**, `local`, **ms\_union**|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes by Usage](../windows/attributes-by-usage.md)   
 [uuid](../windows/uuid-cpp-attributes.md)   
 [dual](../Topic/dual.md)   
 [custom](../windows/custom-cpp.md)   
 [object](../Topic/object%20\(C++\).md)   
 [\_\_interface](../cpp/interface.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)