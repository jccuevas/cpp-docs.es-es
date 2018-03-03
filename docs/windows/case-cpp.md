---
title: caso (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: adacffa4dbce4cc908c393cb5019375234e9ff85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="case-c"></a>case (C++)
Usar con el [switch_type](../windows/switch-type.md) de atributo en un **union**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ case(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *valor*  
 Un valor de entrada posibles para el que desea proporcionar un procesamiento. El tipo de **valor** puede ser uno de los siguientes tipos:  
  
-   `int`  
  
-   `char`  
  
-   `boolean`  
  
-   `enum`  
  
 o un identificador de este tipo.  
  
## <a name="remarks"></a>Comentarios  
 El **caso** atributo C++ tiene la misma funcionalidad que la **caso** atributo MIDL. Este atributo sólo se utiliza con la [switch_type](../windows/switch-type.md) atributo.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra un uso de la **caso** atributo:  
  
```  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Miembro de un **clase** o`struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
