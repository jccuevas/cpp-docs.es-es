---
title: 'serializar_context:: serializar_context | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 02f238a8d9b9d484073794b9a75888325d95107b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399449"
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