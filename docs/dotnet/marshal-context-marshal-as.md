---
title: 'serializar_context:: serializar_as | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cc17010ccccc25679918bc02884774f1644dca69
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379143"
---
# <a name="marshalcontextmarshalas"></a>serializar_context::serializar_as

Realiza el cálculo de referencias en un objeto de datos específicos para convertirla entre administrado y un tipo de datos nativos.

## <a name="syntax"></a>Sintaxis

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Parámetros

*entrada*<br/>
[in] El valor que se desea calcular las referencias a un `To_Type` variable.

## <a name="return-value"></a>Valor devuelto

Una variable de tipo `To_Type` que es el valor convertido de `input`.

## <a name="remarks"></a>Comentarios

Esta función realiza el cálculo de referencias en un objeto de datos específico. Utilice esta función sólo con las conversiones indicadas por la tabla de [Overview of Marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md).

Si se intenta serializar un par de tipos de datos que no son compatibles, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación. Lea el mensaje proporcionado con el error para obtener más información. El error `C4996` se puede generar para algunas funciones, aparte de las desusadas. Se intenta serializar un par de tipos de datos que no son compatibles e intentar usar dos condiciones que se generan el error `marshal_as` para una conversión que requiere un contexto.

La biblioteca de serialización se compone de varios archivos de encabezado. Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones. La tabla de `Marshaling Overview in C++` indica qué archivo de cálculo de referencias debe incluirse en cada conversión.

## <a name="example"></a>Ejemplo

Este ejemplo crea un contexto de cálculo de referencias desde un `System::String` a un `const char *` tipo de variable. Los datos convertidos no serán válidos después de la línea que elimina el contexto.

```
// marshal_context_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   marshal_context^ context = gcnew marshal_context();
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = context->marshal_as<const char*>( message );
   delete context;
   return 0;
}
```

## <a name="requirements"></a>Requisitos

**Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\marshal_windows. h >, \<msclr\marshal_cppstd. h >, o \<msclr\marshal_atl. h >

**Namespace:** msclr:: Interop

## <a name="see-also"></a>Vea también

[Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context (Clase)](../dotnet/marshal-context-class.md)