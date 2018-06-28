---
title: RDX | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.rdx
dev_langs:
- C++
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7647ca56e3159564826efa9caf438456b9ae3568
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878962"
---
# <a name="rdx"></a>rdx
Crea una clave del registro o modifica una clave del registro existente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `key`  
 El nombre de la clave para crear o abrir.  
  
 `valuename`(opcional)  
 Especifica el campo de valor se establezca. Si un campo de valor con este nombre no existe en la clave, se agrega.  
  
 *regtype*  
 El tipo de clave del registro que se va a agregar. Puede ser uno de los siguientes: **texto**, **dword**, **binario**, o `CString`.  
  
## <a name="remarks"></a>Comentarios  
 El **rdx** atributo C++ crea o modifica una clave del registro existente para un componente COM. El atributo agrega una macro BEGIN_RDX_MAP para el objeto que implementa al miembro de destino. `RegistryDataExchange`, una función insertada como resultado de la macro BEGIN_RDX_MAP, se puede utilizar para transferir datos entre el registro y los miembros de datos  
  
 Este atributo se puede usar junto con la [coclase](../windows/coclass.md), [progid](../windows/progid.md), o [vi_progid](../windows/vi-progid.md) atributos u otros atributos que implica una de ellas.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase** o `struct` miembro|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Ejemplo  
 El código siguiente agrega una clave de registro denominada MyValue en el sistema que describe el componente COM CMyClass.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Atributos COM](../windows/com-attributes.md)   
 [registration_script](../windows/registration-script.md)   
