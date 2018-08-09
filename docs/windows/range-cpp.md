---
title: intervalo (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.range
dev_langs:
- C++
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4bf4f02043f3cb11a47357ff91898da23ed03c22
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014213"
---
# <a name="range-c"></a>range (C++)
Especifica un intervalo de valores permitidos para los argumentos o los campos cuyos valores se establecen en tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[ range(  
   low,   
   high  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *low*  
 El valor bajo del intervalo.  
  
 *high*  
 El valor de rango alto.  
  
## <a name="remarks"></a>Comentarios  
 El **intervalo** atributo de C++ tiene la misma funcionalidad que el [intervalo](http://msdn.microsoft.com/library/windows/desktop/aa367151) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cpp_attr_ref_range.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);  
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);  
};  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Método de interfaz, parámetro de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
 [Atributos de miembros de datos](../windows/data-member-attributes.md)   