---
title: "agregados | Microsoft Docs"
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
  - "vc-attr.aggregates"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregates (atributo)"
  - "agregación [C++]"
  - "agregar objetos [C++], atributo aggregates"
  - "agregados [C++]"
ms.assetid: 67a084c9-941f-474b-a029-9c93b38ebe9a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# agregados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica que el objeto agrega el objeto especificado por el CLSID.  
  
## Sintaxis  
  
```  
  
[ aggregates(  
clsid,  
variable_name  
) ]  
  
```  
  
#### Parámetros  
 `clsid`  
 Especifica el CLSID del objeto agregable.  
  
 `variable_name`  
 El nombre de la variable que se va a insertar. Esta variable contiene el elemento **IUnknown** del objeto que se va a agregar.  
  
## Comentarios  
 Cuando se aplica a un objeto, el atributo C\+\+ **aggregates** implementa un contenedor externo para el objeto que se va a agregar \(especificado por `clsid`\).  
  
 Este atributo requiere que el atributo [coclass](../windows/coclass.md), [progid](../Topic/progid.md) o [vi\_progid](../windows/vi-progid.md) \(u otro atributo que implique uno de estos\) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si se aplica **progid**, también se aplicarán **vi\_progid** y **coclass**.  
  
 **Proyectos ATL**  
  
 Si este atributo se usa en un proyecto que usa ATL, el comportamiento del atributo cambiará. Primero se agrega la siguiente entrada al mapa COM del objeto de destino:  
  
```  
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)  
```  
  
 Después, también se agrega la macro [DECLARE\_GET\_CONTROLLING\_UNKNOWN](../Topic/DECLARE_GET_CONTROLLING_UNKNOWN.md).  
  
## Ejemplo  
  
```  
// cpp_attr_ref_aggregates.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
// requires 'aggregatable.dll'  
// see aggregatable attribute to create 'aggregatable.dll'  
class DECLSPEC_UUID("1a8369cc-1c91-42c4-befa-5a5d8c9d2529") CMyClass;  
  
[module (name="MYObject")];  
[object, uuid("ab006d85-e754-47c5-9ef4-2744ff32a20c")]  
__interface IObject  
{  
};  
  
[ coclass, aggregates(__uuidof(CMyClass)),   
  uuid("91cb2c06-8931-432a-baac-206e55c4edfb")]  
struct CObject : IObject  
{  
   int i;  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|Sí|  
|**Atributos requeridos**|Uno o varios de los siguientes: **coclass**, **progid** o **vi\_progid**.|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [COM Attributes](../Topic/COM%20Attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Agregación](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
 [Aggregatable](http://msdn.microsoft.com/library/windows/desktop/aa366721)   
 [COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE\_BLIND](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)