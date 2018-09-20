---
title: 'serializar_context:: ~ serializar_context | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 49f194f153f3e4f911333e22b11ebddf7efcaa32
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447263"
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