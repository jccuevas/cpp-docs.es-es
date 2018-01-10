---
title: satype | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.satype
dev_langs: C++
helpviewer_keywords: satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d4e083cfd0ee1a72992d3c400c4790f5cd50396
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="satype"></a>satype
Especifica el tipo de datos de la **SAFEARRAY** estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ satype(  
   data_type  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *data_type*  
 El tipo de datos para la **SAFEARRAY** estructura de datos que se pasa como parámetro a un método de interfaz.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|Parámetro de interfaz, el método de interfaz|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
## <a name="remarks"></a>Comentarios  
 El **satype** C++ atributo especifica el tipo de datos de la **SAFEARRAY**.  
  
> [!NOTE]
>  Un nivel de direccionamiento indirecto se quita de la **SAFEARRAY** puntero en el archivo .idl generado de cómo se declara en el archivo .cpp.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cpp_attr_ref_satype.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyModule")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A {  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Atributos de compilador](../windows/compiler-attributes.md)   
 [Atributos de parámetro](../windows/parameter-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [identificador](../windows/id.md)   
