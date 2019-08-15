---
title: idl_module (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 8838a833552ae7066dbcf17b4f676d6626c069f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514675"
---
# <a name="idl_module"></a>idl_module

Especifica un punto de entrada en un archivo. dll.

## <a name="syntax"></a>Sintaxis

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>Parámetros

*name*<br/>
Un nombre definido por el usuario para el bloque de código que aparecerá en el archivo. idl.

*dllname*<br/>
Opta El archivo. dll que contiene la exportación.

*uuid*<br/>
Opta IDENTIFICADOR único.

*helpstring*<br/>
Opta Cadena de caracteres utilizada para describir la biblioteca de tipos.

*helpstringcontext*<br/>
Opta IDENTIFICADOR de un tema de ayuda en un archivo. hlp o. chm.

*helpcontext*<br/>
Opta El identificador de la ayuda para esta biblioteca de tipos.

*hidden*<br/>
Opta Parámetro que impide que se muestre la biblioteca. Consulte el atributo MIDL [hidden](/windows/win32/Midl/hidden) para obtener más información.

*restricted*<br/>
Opta No se puede llamar a los miembros de la biblioteca arbitrariamente. Consulte el atributo MIDL [restricted](/windows/win32/Midl/restricted) para obtener más información.

*Declaración de función*<br/>
Función que se va a definir.

## <a name="remarks"></a>Comentarios

El atributo **idl_module** C++ permite especificar el punto de entrada en un archivo. dll, lo que permite importar desde un archivo. dll.

El atributo **idl_module** tiene una funcionalidad similar al atributo MIDL del [módulo](/windows/win32/Midl/module) .

Puede exportar cualquier elemento de un objeto COM que pueda exportar desde un archivo. dll colocando un punto de entrada de DLL en el bloque de biblioteca de un archivo. idl.

Debe usar **idl_module** en dos pasos. En primer lugar, debe definir un par de nombre/DLL. A continuación, al usar **idl_module** para especificar un punto de entrada, especifique el nombre y los atributos adicionales.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo usar el atributo **idl_module** :

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
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[entry](entry.md)