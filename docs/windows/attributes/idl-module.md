---
title: idl_module (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 80e4909a61b5b53ecde19471f2c838dd4c425874
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034983"
---
# <a name="idlmodule"></a>idl_module

Especifica un punto de entrada en un archivo .dll.

## <a name="syntax"></a>Sintaxis

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>Parámetros

*name*<br/>
Un nombre definido por el usuario para el bloque de código que va a aparecer en el archivo. idl.

*dllname*<br/>
(Opcional) El archivo .dll que contiene la exportación.

*uuid*<br/>
(Opcional) Un identificador único.

*helpstring*<br/>
(Opcional) Una cadena de caracteres que se usa para describir la biblioteca de tipos.

*helpstringcontext*<br/>
(Opcional) El identificador de un tema de ayuda en un archivo .hlp o chm.

*helpcontext*<br/>
(Opcional) Identificador de ayuda para esta biblioteca de tipos.

*hidden*<br/>
(Opcional) Un parámetro que impide que aparezca la biblioteca. Consulte el atributo MIDL [hidden](/windows/desktop/Midl/hidden) para obtener más información.

*restricted*<br/>
(Opcional) Los miembros de la biblioteca no se puede llamar arbitrariamente. Consulte el atributo MIDL [restricted](/windows/desktop/Midl/restricted) para obtener más información.

*declaración de función*<br/>
La función que va a definir.

## <a name="remarks"></a>Comentarios

El **idl_module** C++ atributo permite especificar el punto de entrada en un archivo .dll, que permite importar desde un archivo DLL.

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

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[entry](entry.md)