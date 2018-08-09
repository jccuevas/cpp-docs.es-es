---
title: idl_module | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_module
dev_langs:
- C++
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ff8353bef24aa772621cee611519a8e7ab659af
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012120"
---
# <a name="idlmodule"></a>idl_module
Especifica un punto de entrada en un archivo .dll.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[ idl_module (   
   name=module_name,   
   dllname=dll,   
   uuid="uuid",   
   helpstring="help text",   
   helpstringcontext=helpcontextID,   
   helpcontext=helpcontext,   
   hidden,   
   restricted  
) ]  
function declaration  
```  
  
### <a name="parameters"></a>Parámetros  
 *name*  
 Un nombre definido por el usuario para el bloque de código que va a aparecer en el archivo. idl.  
  
 *dllname* (opcional)  
 El archivo .dll que contiene la exportación.  
  
 *UUID* (opcional)  
 Identificador único.  
  
 *helpstring* (opcional)  
 Una cadena de caracteres que se usa para describir la biblioteca de tipos.  
  
 *helpstringcontext* (opcional)  
 El identificador de un tema de ayuda en un archivo .hlp o chm.  
  
 *HelpContext* (opcional)  
 Identificador de ayuda para esta biblioteca de tipos.  
  
 *oculto* (opcional)  
 Un parámetro que impide que aparezca la biblioteca. Consulte el atributo MIDL [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) para obtener más información.  
  
 *restringido* (opcional)  
 Los miembros de la biblioteca no se puede llamar arbitrariamente. Consulte el atributo MIDL [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) para obtener más información.  
  
 *declaración de función*  
 La función que va a definir.  
  
## <a name="remarks"></a>Comentarios  
 El **idl_module** atributo de C++ le permite especificar el punto de entrada en un archivo .dll, que permite importar desde un archivo DLL.  
  
 El **idl_module** atributo tiene una funcionalidad similar a la [módulo](http://msdn.microsoft.com/library/windows/desktop/aa367099) atributo MIDL.  
  
 Puede exportar cualquier cosa desde un objeto COM que se puede exportar desde un archivo .dll colocando un punto de entrada del archivo DLL en el bloque de biblioteca de un archivo. idl.  
  
 Su debe usar **idl_module** en dos pasos. En primer lugar, debe definir un par de nombre o DLL. A continuación, cuando utilice **idl_module** para especificar un punto de entrada, especifique el nombre y los atributos adicionales.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo usar el **idl_module** atributo:  
  
```cpp  
// cpp_attr_ref_idl_module.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];  
[idl_module(name="MyLib"), entry(4), usesgetlasterror]  
void FuncName(int i);  
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
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
 [entry](../windows/entry.md)   