---
title: serializar_context (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fc3399ee088a0430ca857c3e421742ee484d337a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413321"
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