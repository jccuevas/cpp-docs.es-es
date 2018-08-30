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
ms.openlocfilehash: 9fc3be9fb25b6593f4b69f846394544b7b7d756a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220470"
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
Un parámetro que impide que aparezca la biblioteca. Consulte la [oculto](/windows/desktop/Midl/hidden) atributo MIDL para obtener más información.

*restringido* (opcional)  
Los miembros de la biblioteca no se puede llamar arbitrariamente. Consulte la [restringido](/windows/desktop/Midl/restricted) atributo MIDL para obtener más información.

*declaración de función*  
La función que va a definir.

## <a name="remarks"></a>Comentarios

El **idl_module** atributo de C++ le permite especificar el punto de entrada en un archivo .dll, que permite importar desde un archivo DLL.

El **idl_module** atributo tiene una funcionalidad similar a la [módulo](/windows/desktop/Midl/module) atributo MIDL.

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