---
title: idl_module | Documentos de Microsoft
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
ms.openlocfilehash: 11547a3fb1bd46a1e2edb8ce9dd0a6547464f796
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="idlmodule"></a>idl_module
Especifica un punto de entrada en un archivo DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
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
  
#### <a name="parameters"></a>Parámetros  
 **name**  
 Un nombre definido por el usuario para el bloque de código que va a aparecer en el archivo IDL.  
  
 **nombre dll** (opcional)  
 El archivo .dll que contiene la exportación.  
  
 `uuid` (opcional)  
 Identificador único.  
  
 **helpstring** (opcional)  
 Una cadena de caracteres que se usa para describir la biblioteca de tipos.  
  
 **helpstringcontext** (opcional)  
 El identificador de un tema de ayuda en un archivo .hlp o .chm.  
  
 **helpcontext** (opcional)  
 Identificador de ayuda para esta biblioteca de tipos.  
  
 **hidden** (opcional)  
 Un parámetro que impide que la biblioteca que se va a mostrar. Consulte el atributo MIDL [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) para obtener más información.  
  
 ***restringido*** (opcional)  
 Los miembros de la biblioteca no se puede llamar de forma arbitraria. Consulte el atributo MIDL [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) para obtener más información.  
  
 *declaración de función*  
 La función que va a definir.  
  
## <a name="remarks"></a>Comentarios  
 El `idl_module` atributo C++ le permite especificar el punto de entrada en un archivo .dll, que le permite importar desde un archivo DLL.  
  
 El **idl_module** atributo tiene una funcionalidad similar a la [módulo](http://msdn.microsoft.com/library/windows/desktop/aa367099) atributo MIDL.  
  
 Puede exportar nada de un objeto COM que se puede exportar desde un archivo .dll colocando un punto de entrada DLL en el bloque de biblioteca de un archivo IDL.  
  
 La debe usar `idl_module` en dos pasos. En primer lugar, debe definir un par nombre/DLL. A continuación, cuando usa `idl_module` para especificar un punto de entrada, especifique el nombre y los atributos adicionales.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo utilizar el `idl_module` atributo:  
  
```  
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
