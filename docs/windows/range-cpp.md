---
title: intervalo (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.range
dev_langs:
- C++
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b95b1bfd093a12bca5398c266d6a7c8236140105
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="range-c"></a>range (C++)
Especifica un intervalo de valores permitidos para argumentos o los campos cuyos valores se establecen en tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ range(  
   low,   
   high  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *low*  
 El valor bajo del intervalo.  
  
 *high*  
 El valor de rango alto.  
  
## <a name="remarks"></a>Comentarios  
 El **intervalo** atributo C++ tiene la misma funcionalidad que la [intervalo](http://msdn.microsoft.com/library/windows/desktop/aa367151) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
