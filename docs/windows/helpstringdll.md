---
title: helpstringdll | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1eecedca8988c95466a3f257fbc77768b7c67b3b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392871"
---
# <a name="helpstringdll"></a>helpstringdll

Especifica el nombre del archivo DLL a utilizar para realizar la búsqueda de cadenas de documento (localización).

## <a name="syntax"></a>Sintaxis

```cpp
[ helpstringdll(
   "string"
) ]
```

### <a name="parameters"></a>Parámetros

*string*<br/>
DLL que se va a utilizar para realizar la búsqueda de cadenas de documento.

## <a name="remarks"></a>Comentarios

El **helpstringdll** atributo de C++ tiene la misma funcionalidad que el [helpstringdll](/windows/desktop/Midl/helpstringdll) atributo MIDL.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **interfaz**, método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de interfaz](../windows/interface-attributes.md)<br/>
[Atributos de clase](../windows/class-attributes.md)<br/>
[Atributos de método](../windows/method-attributes.md)  