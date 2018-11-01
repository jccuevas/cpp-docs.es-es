---
title: serializar_context::~serializar_context
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
ms.openlocfilehash: 3bf16ab2dde4047fb845cd700821d097f733a4d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528224"
---
# <a name="marshalcontextmarshalcontext"></a>serializar_context::~serializar_context

Destruye un objeto `marshal_context`.

## <a name="syntax"></a>Sintaxis

```
~marshal_context();
```

## <a name="remarks"></a>Comentarios

Algunas conversiones de datos requieren un contexto de cálculo de referencias. Consulte [Overview of Marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de qué traducciones requieren un contexto y qué archivo de cálculo de referencias debe incluirse en la aplicación.

Eliminar un `marshal_context` objeto invalidará los datos convertidos por ese contexto. Si desea conservar los datos después de un `marshal_context` se destruye el objeto, debe copiar manualmente los datos a una variable que se conservará.

## <a name="requirements"></a>Requisitos

**Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\marshal_windows. h >, \<msclr\marshal_cppstd. h >, o \<msclr\marshal_atl. h >

**Namespace:** msclr:: Interop

## <a name="see-also"></a>Vea también

[Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context (Clase)](../dotnet/marshal-context-class.md)