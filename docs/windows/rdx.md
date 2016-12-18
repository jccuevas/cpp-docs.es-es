---
title: "rdx | Microsoft Docs"
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
  - "vc-attr.rdx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rdx attribute"
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# rdx
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea una clave del Registro o modifica una clave del Registro existente.  
  
## Sintaxis  
  
```  
  
      [ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
#### Parámetros  
 `key`  
 El nombre de la clave que se va a crear o abierta.  
  
 `valuename`\(opcional\)  
 Especifica el campo Valor que se va a establecer.  Si un campo Valor con este nombre no existe en la clave, se agrega.  
  
 *regtype*  
 El tipo de clave del Registro que se está agregando.  Puede ser: **texto**, **DWORD**, **binario**, o `CString`.  
  
## Comentarios  
 El atributo de **rdx** C\+\+ crea o modifica una clave del Registro existente para un componente COM.  El atributo agrega una macro de BEGIN\_RDX\_MAP al objeto que implementa el miembro de destino.  `RegistryDataExchange`, una función inline como resultado de la macro de BEGIN\_RDX\_MAP, se puede utilizar para transferir datos entre el registro y los miembros de datos  
  
 Este atributo se utiliza junto con [CoClass](../windows/coclass.md), [ProgID](../Topic/progid.md), o los atributos de [vi\_progid](../windows/vi-progid.md) u otros atributos que requiere uno.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase** o miembro de `struct`|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Ejemplo  
 El código siguiente agrega una clave del Registro denominada MyValue al sistema que describe el componente de CMyClass COM.  
  
```  
// cpp_attr_ref_rdx.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
  
[module (name="MyLib")];  
  
class CMyClass {  
public:  
   CMyClass() {  
      strcpy_s(m_sz, "SomeValue");  
   }  
  
   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]   
   char m_sz[256];  
};  
```  
  
## Vea también  
 [COM Attributes](../Topic/COM%20Attributes.md)   
 [registration\_script](../windows/registration-script.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)