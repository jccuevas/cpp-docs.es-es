---
title: includelib (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e10ab341dc4c90a26315ea5e30f03bc71e628b64
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603386"
---
# <a name="includelib-c"></a>includelib (C++)
Hace que un archivo IDL o .h para incluirse en el archivo .idl generado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ includelib(  
   name.idl  
) ];  
```  
  
### <a name="parameters"></a>Parámetros  
 *Name.idl*  
 El nombre del archivo .idl que desee incluir como parte del archivo .idl generado.  
  
## <a name="remarks"></a>Comentarios  
 El **includelib** atributo de C++ hace que un archivo IDL o .h para incluirse en el archivo .idl generado después de la `importlib` instrucción.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente se muestra en un archivo. cpp:  
  
```cpp  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|Sí|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
 [Importación](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [incluir](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   