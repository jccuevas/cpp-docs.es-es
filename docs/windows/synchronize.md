---
title: "synchronize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.synchronize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "synchronize attribute"
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# synchronize
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Sincronizar el acceso al método de destino.  
  
## Sintaxis  
  
```  
  
[synchronize]  
  
```  
  
## Comentarios  
 El atributo de **sincronizar** C\+\+ implementa compatibilidad para sincronizar el método de destino de un objeto.  La sincronización permite que varios objetos utilizan un recurso común \(como un método de una clase\) controlar el acceso del método de destino.  
  
 El código insertado por este atributo llama al método adecuado de `Lock` \(determina el modelo de subprocesos\) al principio del método de destino.  Cuando se sale del método, `Unlock` automáticamente se denomina.  Para obtener más información sobre estas funciones, vea [CComAutoThreadModule:: bloqueo](../Topic/CComAutoThreadModule::Lock.md)  
  
 Este atributo requiere que [CoClass](../windows/coclass.md), [ProgID](../Topic/progid.md), o el atributo de [vi\_progid](../windows/vi-progid.md) \(u otro atributo que implica una de estas\) también se aplican al mismo elemento.  Si se utiliza cualquier atributo único, los otros dos se aplica automáticamente.  por ejemplo, si se aplica **ProgID** , **vi\_progid** y **CoClass** también se aplican.  
  
## Ejemplo  
 El código siguiente proporciona la sincronización del método de `UpdateBalance` del objeto de `CMyClass` .  
  
```  
// cpp_attr_ref_synchronize.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="SYNC")];  
  
[coclass,  
 threading(both),  
 vi_progid("MyProject.MyClass"),  
 progid("MyProject.MyClass.1"),  
 uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")  
]  
class CMyClass {  
   float m_nBalance;  
  
   [synchronize]  
   void UpdateBalance(float nAdjust) {  
      m_nBalance += nAdjust;  
   }  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|método de clase, método|  
|**repetible**|No|  
|**Atributos necesarios**|Uno o más de los siguientes: **CoClass**, **ProgID**, o **vi\_progid**.|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [COM Attributes](../Topic/COM%20Attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)