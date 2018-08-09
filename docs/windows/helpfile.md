---
title: HelpFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c2714c1418c5c9828322561ae1d7ca86dc6130a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647741"
---
# <a name="helpfile"></a>helpfile
Establece el nombre del archivo de ayuda para una biblioteca de tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[ helpfile(  
   "filename"  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *filename*  
 El nombre del archivo que contiene los temas de ayuda.  
  
## <a name="remarks"></a>Comentarios  
 El **helpfile** atributo de C++ tiene la misma funcionalidad que el [helpfile](http://msdn.microsoft.com/library/windows/desktop/aa366853) atributo MIDL.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [módulo](../windows/module-cpp.md) para obtener un ejemplo de cómo usar **helpfile**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**interfaz**, **typedef**, **clase**, método, **propiedad**|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Atributos de método](../windows/method-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [HelpContext](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   