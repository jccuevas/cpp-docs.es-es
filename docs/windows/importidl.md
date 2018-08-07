---
title: importidl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd930ef70e5bb2b87c584c1d821cdf4528580a31
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607188"
---
# <a name="importidl"></a>importidl
Inserta el archivo .idl especificado en el archivo .idl generado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[ importidl(  
   idl_file  
) ];  
```  
  
### <a name="parameters"></a>Parámetros  
 *idl_file*  
 Identifica el nombre del archivo .idl que desea combinar con el archivo .idl que se generará para la aplicación.  
  
## <a name="remarks"></a>Comentarios  
 El **importidl** atributo de C++ coloca la sección fuera del bloque de biblioteca (en *idl_file*) en el archivo .idl generado del programa y la sección de biblioteca (en *idl_file*) en la biblioteca de la sección de su programa genera el archivo .idl.  
  
 Es posible que desee usar **importidl**, por ejemplo, si desea usar un archivo .idl codificadas con el archivo .idl generado.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cpp_attr_ref_importidl.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importidl("import.idl")];  
```  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos de compilador](../windows/compiler-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
 [Importación](../windows/import.md)   
 [importlib](../windows/importlib.md)   
 [incluir](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   