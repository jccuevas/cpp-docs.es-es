---
title: serializar_context::serializar_context
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
ms.openlocfilehash: a1a62c47450224aa2bcacde75038adf7a8cfbb9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532592"
---
# <a name="marshalcontextmarshalcontext"></a>serializar_context::serializar_context

Construye un `marshal_context` objeto va a usar para la conversión de datos entre los tipos de datos administrados y nativos.

## <a name="syntax"></a>Sintaxis

```
marshal_context();
```

## <a name="remarks"></a>Comentarios

Algunas conversiones de datos requieren un contexto de cálculo de referencias. Consulte [Overview of Marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de qué traducciones requieren un contexto y qué archivo de cálculo de referencias debe incluirse en la aplicación.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [serializar_context:: serializar_as](../dotnet/marshal-context-marshal-as.md).

## <a name="requirements"></a>Requisitos

**Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\marshal_windows. h >, \<msclr\marshal_cppstd. h >, o \<msclr\marshal_atl. h >

**Namespace:** msclr:: Interop

## <a name="see-also"></a>Vea también

[Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context (Clase)](../dotnet/marshal-context-class.md)