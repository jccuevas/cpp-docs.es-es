---
title: satype | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 462dba3caaef53e49203eab6d006ea59d7b23c0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590378"
---
# <a name="satype"></a>satype

Especifica el tipo de datos de la `SAFEARRAY` estructura.

## <a name="syntax"></a>Sintaxis

```cpp
[ satype(
   data_type
) ]
```

### <a name="parameters"></a>Parámetros

*data_type*  
Tipo de datos de la `SAFEARRAY` estructura de datos que se pasa como parámetro a un método de interfaz.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

## <a name="remarks"></a>Comentarios

El **satype** atributo de C++ especifica el tipo de datos de la `SAFEARRAY`.

> [!NOTE]
> Un nivel de direccionamiento indirecto se quita de la `SAFEARRAY` puntero en el archivo .idl generado de forma se declara en el archivo .cpp.

## <a name="example"></a>Ejemplo

```cpp
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