---
title: serializar_as
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2b2cacb0acf04aa40b3e299bffd7357e04916b16
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544848"
---
# <a name="marshal_as"></a>serializar_as

Este método convierte los datos entre los entornos nativo y administrado.

## <a name="syntax"></a>Sintaxis

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Parámetros

*input*<br/>
de Valor que se desea serializar en una variable de `To_Type`.

## <a name="return-value"></a>Valor devuelto

Una variable de tipo `To_Type` que es el valor convertido de `input`.

## <a name="remarks"></a>Observaciones

Este método es una manera simplificada de convertir datos entre los tipos nativos y administrados. Para determinar qué tipos de datos se admiten, consulte [información general sobre C++el cálculo de referencias en ](../dotnet/overview-of-marshaling-in-cpp.md). Algunas conversiones de datos requieren un contexto. Puede convertir esos tipos de datos mediante la [clase marshal_context](../dotnet/marshal-context-class.md).

Si intenta calcular las referencias de un par de tipos de datos que no se admiten, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación. Lea el mensaje proporcionado con el error para obtener más información. El error `C4996` se puede generar para algunas funciones, aparte de las que están en desuso. Un ejemplo de esto consiste en intentar para serializar un par de tipos de datos que no se admiten.

La biblioteca de cálculo de referencias se compone de varios archivos de encabezado. Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones. Para ver qué conversiones están asociadas con qué archivos, consulte la tabla de `Marshaling Overview`. Independientemente de la conversión que desee hacer, el requisito de espacio de nombres siempre está en vigor.

Produce `System::ArgumentNullException(_EXCEPTION_NULLPTR)` si el parámetro de entrada es NULL.

## <a name="example"></a>Ejemplo

Este ejemplo calcula las referencias de `const char*` para un tipo de variable `System::String`.

```cpp
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>Requisitos

**Archivo de encabezado:** \<msclr\marshal.h >, \<msclr \ marshal_windows. h >, \<msclr \ marshal_cppstd. h > o \<msclr \ marshal_atl. h >

**Espacio de nombres:** msclr:: Interop

## <a name="see-also"></a>Consulte también

[Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context (Clase)](../dotnet/marshal-context-class.md)
