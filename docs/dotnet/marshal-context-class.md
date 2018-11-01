---
title: serializar_context (Clase)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_context
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 0e25aee0996b0cd16ca92566da22d377b762d7bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594537"
---
# <a name="marshalcontext-class"></a>serializar_context (Clase)

Esta clase convierte datos entre los entornos nativos y administrados.

## <a name="syntax"></a>Sintaxis

```
class marshal_context
```

## <a name="remarks"></a>Comentarios

Use la `marshal_context` clase para las conversiones de datos que requieren un contexto. Consulte [Overview of Marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de qué conversiones requieren un contexto y qué archivo de cálculo de referencias debe incluirse. El resultado del cálculo de referencias cuando se usa un contexto es válido solo hasta el `marshal_context` se destruye el objeto. Para conservar su resultado, debe copiar los datos.

El mismo `marshal_context` puede usarse para varias conversiones de datos. Volver a usar el contexto de esta manera no afectará a los resultados de las llamadas de serialización anteriores.

## <a name="requirements"></a>Requisitos

**Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\marshal_windows. h >, \<msclr\marshal_cppstd. h >, o \<msclr\marshal_atl. h >

**Namespace:** msclr:: Interop

## <a name="see-also"></a>Vea también

[Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)