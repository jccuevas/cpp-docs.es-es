---
title: "iid_is | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.iid_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iid_is attribute"
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# iid_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el IID de la interfaz COM indicada por un puntero de interfaz.  
  
## Sintaxis  
  
```  
  
      [ iid_is(  
   "expression"  
) ]  
```  
  
#### Parámetros  
 *expresión*  
 La expresión programado c. que especifica un identificador IID de interfaz COM que por un puntero de interfaz.  
  
## Comentarios  
 el atributo de **iid\_is** C\+\+ tiene la misma funcionalidad que el atributo de [iid\_is](http://msdn.microsoft.com/library/windows/desktop/aa367044) MIDL.  
  
## Ejemplo  
 el código siguiente muestra el uso de **iid\_is**:  
  
```  
// cpp_attr_ref_iid_is.cpp  
// compile with: /LD  
#include "wtypes.h"  
#include "unknwn.h"  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]   
   IUnknown ** ppvObject);  
};  
  
[module(name="ATLFIRELib")];  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Parámetros de la interfaz, un miembro de datos|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)