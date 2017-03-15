---
title: "threading (C++) | Microsoft Docs"
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
  - "vc-attr.threading"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "threading attribute"
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# threading (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el modelo de subprocesos de un objeto COM.  
  
## Sintaxis  
  
```  
  
      [ threading(  
   model=enumeration  
) ]  
```  
  
#### Parámetros  
 ***modelo*** \(opcional\)  
 uno de los modelos de subprocesos siguientes:  
  
-   **apartamento** \(subproceso controlado\)  
  
-   **neutro** \(componentes de .NET Framework sin interfaz de usuario\)  
  
-   **solo** \(subprocesamiento simple\)  
  
-   **libre** \(subprocesamiento libre\)  
  
-   **ambos** \(apartamento y subprocesamiento libre\)  
  
 el valor predeterminado es **apartamento**.  
  
## Comentarios  
 El atributo de **subprocesamiento** C\+\+ no aparece en el archivo generado .idl pero se utiliza en la implementación del objeto COM.  
  
 En proyectos ATL, si el atributo de [CoClass](../windows/coclass.md) también está presente, el modelo de subprocesos especificado por *el modelo* se pasa como parámetro de plantilla a la clase de [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) , insertada por el atributo de **CoClass** .  
  
 Las restricciones de **subprocesamiento** también tienen acceso a [event\_source](../windows/event-source.md).  
  
## Ejemplo  
 Vea el ejemplo de [licencia](../windows/licensed.md) para un ejemplo de uso de **subprocesamiento**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|**CoClass**|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [COM Attributes](../Topic/COM%20Attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Compatibilidad del código antiguo con multithreading \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Neutral Apartments](http://msdn.microsoft.com/library/windows/desktop/ms681813)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)