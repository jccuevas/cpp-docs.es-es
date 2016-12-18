---
title: "support_error_info | Microsoft Docs"
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
  - "vc-attr.support_error_info"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "support_error_info (atributo)"
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# support_error_info
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Implementa compatibilidad para devolver errores detallados.  
  
## Sintaxis  
  
```  
  
[ support_error_info(  
   error_interface=  
uuid  
) ]  
  
```  
  
#### Parámetros  
 **error\_interface**  
 Identificador de la interfaz que implementa **IErrorInfo**.  
  
## Comentarios  
 El atributo de C\+\+ **support\_error\_info** implementa compatibilidad para devolver al cliente errores detallados y contextuales detectados por el objeto de destino. Para que el objeto sea compatible con los errores, el objeto debe implementar los métodos de la interfaz **IErrorInfo**. Para obtener más información, consulte [Compatibilidad con IDispatch e IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md).  
  
 Este atributo agrega la clase [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) como una clase base al objeto de destino. El resultado es una implementación predeterminada de **ISupportErrorInfo** que se puede usar cuando una sola interfaz genera errores en un objeto.  
  
## Ejemplo  
 El código siguiente agrega compatibilidad predeterminada con la interfaz **ISupportErrorInfo** al objeto `CMyClass`.  
  
```  
// cpp_attr_ref_support_error_info.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="mymod")];  
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]  
__interface IMyErrors  
{  
};  
  
[ coclass, support_error_info("IMyErrors"),  
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]  
class CMyClass  
{  
};  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**|  
|**Reiterativo**|Sí|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [COM Attributes](../Topic/COM%20Attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)