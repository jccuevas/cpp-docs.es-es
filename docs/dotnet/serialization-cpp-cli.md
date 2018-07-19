---
title: Serialización (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f4a410da74c37ee722c04f21e2cde906b9d061d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164574"
---
# <a name="serialization-ccli"></a>Serialización (C++/CLI)
Serialización (el proceso de almacenar el estado de un objeto o miembro en un soporte permanente) de las clases administradas (incluyendo campos y propiedades individuales) es compatible con la <xref:System.SerializableAttribute> y <xref:System.NonSerializedAttribute> clases.  
  
## <a name="remarks"></a>Comentarios  
 Aplicar el **SerializableAttribute** atributo personalizado a una clase administrada para serializar la clase completa o se aplican sólo a determinados campos o propiedades para serializar los elementos de la clase administrada. Use la **NonSerializedAttribute** atributo personalizado para excluir campos o propiedades de una clase administrada desde la que se está serializando.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente, la clase `MyClass` (y la propiedad `m_nCount`) está marcado como serializable. Sin embargo, el `m_nData` no se serializa la propiedad tal y como indica la **NonSerialized** atributos personalizados:  
  
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
 Tenga en cuenta que se pueden hacer referencia a los dos atributos utilizando su "nombre corto" (**Serializable** y **NonSerialized**). Esto se explica con más detalle en [aplicar atributos](/dotnet/standard/attributes/applying-attributes).  
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)