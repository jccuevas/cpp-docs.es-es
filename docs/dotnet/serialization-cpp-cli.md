---
title: Serialización (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: 794a71ae9a146b691ba6a4377a7fdf2c3ddd3501
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741391"
---
# <a name="serialization-ccli"></a>Serialización (C++/CLI)

Serialización (el proceso de almacenar el estado de un objeto o miembro en un medio permanente) de las clases administradas (incluyendo campos y propiedades individuales) es compatible con la <xref:System.SerializableAttribute> y <xref:System.NonSerializedAttribute> clases.

## <a name="remarks"></a>Comentarios

Aplicar el **SerializableAttribute** atributo personalizado a una clase administrada para serializar la clase completa o se aplican a determinados campos o propiedades para serializar las partes de la clase administrada. Use la **NonSerializedAttribute** atributo personalizado para excluir campos o propiedades de una clase administrada desde la que se está serializando.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente, la clase `MyClass` (y la propiedad `m_nCount`) está marcado como serializable. Sin embargo, el `m_nData` no se serializa la propiedad tal y como indica la **NonSerialized** atributo personalizado:

### <a name="code"></a>Código

```
// serialization_and_mcpp.cpp
// compile with: /LD /clr
using namespace System;

[ Serializable ]
public ref class MyClass {
public:
   int m_nCount;
private:
   [ NonSerialized ]
   int m_nData;
};
```

### <a name="comments"></a>Comentarios

Tenga en cuenta que se pueden hacer referencia a ambos atributos utilizando su "nombre corto" (**Serializable** y **NonSerialized**). Esto se explica más en [aplicar atributos](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Vea también

[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
