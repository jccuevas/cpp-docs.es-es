---
title: "vi_progid | Microsoft Docs"
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
  - "vc-attr.vi_progid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vi_progid attribute"
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vi_progid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

especifica un formulario de la versión\-independiente de ProgID.  
  
## Sintaxis  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### Parámetros  
 *name*  
 la versión\-independiente ProgID que representa el objeto.  
  
 Muestra de Progid una versión legible del identificador de clase \(CLSID\) utilizado para identificar objetos COM Y ActiveX.  
  
## Comentarios  
 El atributo de **vi\_progid** C\+\+ permite especificar una versión\-independiente ProgID para un objeto COM.  ProgID tiene el formato *name1.name2.version*.  una versión\-independiente ProgID no tiene una *versión*.  Es posible especificar **ProgID** y los atributos de **vi\_progid** en la coclase.  Si no especifica **vi\_progid**, la versión\-independiente ProgID es el valor especificado por el atributo de [ProgID](../Topic/progid.md) .  
  
 **vi\_progid** implica el atributo de **CoClass** , es decir, si se especifica **vi\_progid**, es lo mismo que especificar atributos de **CoClass** y de **vi\_progid** .  
  
 El atributo de **vi\_progid** genera una clase automáticamente que se registre con un nombre especificado.  El archivo generado .idl no mostrará el valor de Id.  
  
 En proyectos ATL, si el atributo de [CoClass](../windows/coclass.md) también está presente, ProgID especificado es utilizado por la función de **GetVersionIndependentProgID** \(insertada por el atributo de **CoClass** \).  
  
## Ejemplo  
 Vea el ejemplo de [CoClass](../windows/coclass.md) para un ejemplo de uso de **vi\_progid**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [ProgID Key](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)