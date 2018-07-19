---
title: support_error_info | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.support_error_info
dev_langs:
- C++
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c366a379d15e50aabdc3c2157f57f85b6b5b33b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889935"
---
# <a name="supporterrorinfo"></a>support_error_info
Implementa compatibilidad para devolver errores detallados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ support_error_info(  
   error_interface=uuid  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 **error_interface**  
 Identificador de la interfaz que implementa **IErrorInfo**.  
  
## <a name="remarks"></a>Comentarios  
 El atributo de C++ **support_error_info** implementa compatibilidad para devolver al cliente errores detallados y contextuales detectados por el objeto de destino. Para que el objeto sea compatible con los errores, el objeto debe implementar los métodos de la interfaz **IErrorInfo** . Para obtener más información, consulte [Compatibilidad con IDispatch e IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md).  
  
 Este atributo agrega la clase [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) como una clase base al objeto de destino. El resultado es una implementación predeterminada de **ISupportErrorInfo** que se puede usar cuando una sola interfaz genera errores en un objeto.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente agrega compatibilidad predeterminada con la interfaz **ISupportErrorInfo** al objeto `CMyClass` .  
  
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
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**|  
|**Reiterativo**|Sí|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos COM](../windows/com-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
