---
title: COM_INTERFACE_ENTRY (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.com_interface_entry
dev_langs:
- C++
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0fb7de1987d77f19e04f867aac68cbcc67c1f1e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863457"
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)
Agrega una entrada de la interfaz en el mapa COM de la clase de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
     [ com_interface_entry(   
  com_interface_entry  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *COM_INTERFACE_ENTRY*  
 Una cadena que contiene el texto real de la entrada. Para obtener una lista de valores posibles, consulte [Macros COM_INTERFACE_ENTRY](../atl/reference/com-interface-entry-macros.md).  
  
## <a name="remarks"></a>Comentarios  
 El `com_interface_entry` el contenido de una cadena de caracteres íntegra de inserciones de atributos de C++ en el mapa de interfaz COM del objeto de destino. Si el atributo se aplica una vez que el objeto de destino, la entrada se inserta en el principio de la asignación de interfaz existente. Si se aplica el atributo varias veces al mismo objeto de destino, las entradas se insertan al principio de la asignación de interfaz en el orden en que se reciben.  
  
 Este atributo requiere que el atributo [coclass](../windows/coclass.md), [progid](../windows/progid.md)o [vi_progid](../windows/vi-progid.md) (u otro atributo que implique uno de estos) se aplique también al mismo elemento. Si se usa cualquier atributo único, los otros dos se aplicarán automáticamente. Por ejemplo, si se aplica **progid** , también se aplicarán **vi_progid** y **coclass** .  
  
 Dado que el primer uso de `com_interface_entry` hace que la nueva interfaz va a insertar al principio de la asignación de interfaz, debe ser uno de los siguientes tipos COM_INTERFACE_ENTRY:  
  
-   COM_INTERFACE_ENTRY  
  
-   COM_INTERFACE_ENTRY_IID  
  
-   COM_INTERFACE_ENTRY2  
  
-   COM_INTERFACE_ENTRY2_IID  
  
 Usos adicionales de la `com_interface_entry` atributo puede usar todos los tipos COM_INTERFACE_ENTRY.  
  
 Esta restricción es necesaria porque ATL usa la primera entrada en el mapa de interfaz como identidad **IUnknown**; por lo tanto, la entrada debe ser una interfaz válida. Por ejemplo, el ejemplo de código siguiente es válido porque la primera entrada en el mapa de interfaz no especifica una interfaz COM real.  
  
```  
[ coclass, com_interface_entry =  
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"  
]  
   class CMyClass  
   {  
   };  
```  
  
## <a name="example"></a>Ejemplo  
 El código siguiente agrega dos entradas para el mapa de interfaz COM existente de **CMyBaseClass**. La primera es una interfaz estándar, y la segunda oculta la **IDebugTest** interfaz.  
  
```  
// cpp_attr_ref_com_interface_entry.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name ="ldld")];  
  
[ object,  
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]  
__interface IDebugTest{};  
  
[ object,  
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]  
__interface IMyClass{};  
  
[ coclass,  
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),  
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),  
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")  
]  
  
class CMyClass: public IMyClass, public IDebugTest  
{  
};  
```  
  
 El mapa de objetos COM resultante para **CMyBaseClass** es como sigue:  
  
```  
BEGIN_COM_MAP(CMyClass)  
    COM_INTERFACE_ENTRY (IMyClass)  
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)  
    COM_INTERFACE_ENTRY(IMyClass)  
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)  
    COM_INTERFACE_ENTRY(IDebugTest)  
    COM_INTERFACE_ENTRY(IProvideClassInfo)  
END_COM_MAP()  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|Sí|  
|**Atributos requeridos**|Uno o varios de los siguientes: **coclass**, **progid**o **vi_progid**.|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos COM](../windows/com-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Typedef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
