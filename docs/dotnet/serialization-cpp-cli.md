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
ms.openlocfilehash: b2dfdcaf1a1f33e89d106d4529ffc9af2d08376b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545166"
---
# <a name="serialization-ccli"></a>Serialización (C++/CLI)

La serialización (el proceso de almacenar el estado de un objeto o miembro en un medio permanente) de las clases administradas (incluidas las propiedades o campos individuales) es compatible con las clases <xref:System.SerializableAttribute> y <xref:System.NonSerializedAttribute>.

## <a name="remarks"></a>Observaciones

Aplique el atributo personalizado **SerializableAttribute** a una clase administrada para serializar la clase completa o aplicar solo a campos o propiedades específicos para serializar partes de la clase administrada. Utilice el atributo personalizado **NonSerializedAttribute** para excluir los campos o las propiedades de una clase administrada de la serialización.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente, la clase `MyClass` (y la propiedad `m_nCount`) se marca como serializable. Sin embargo, la propiedad `m_nData` no se serializa como se indica en el atributo personalizado no **serializado** :

### <a name="code"></a>Código

```cpp
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

Tenga en cuenta que se puede hacer referencia a ambos atributos mediante su "nombre corto" (**serializable** y no **serializado**). Esto se explica con más detalle en la [aplicación de atributos](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Consulte también

[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
