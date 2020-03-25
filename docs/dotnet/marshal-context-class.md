---
title: serializar_context (Clase)
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- msclr::marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 146a0f7a7cc1402f7c28e6bf09fead1914c7c6be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208537"
---
# <a name="marshal_context-class"></a>serializar_context (Clase)

Esta clase convierte los datos entre entornos nativos y administrados.

## <a name="syntax"></a>Sintaxis

```cpp
class marshal_context
```

## <a name="remarks"></a>Observaciones

Utilice la clase `marshal_context` para las conversiones de datos que requieren un contexto. Para obtener más información sobre las conversiones que requieren un contexto y el archivo de serialización que se debe incluir, vea [información general sobre C++el cálculo de referencias en ](../dotnet/overview-of-marshaling-in-cpp.md). El resultado de la serialización cuando se utiliza un contexto solo es válido hasta que se destruya el objeto de `marshal_context`. Para conservar el resultado, debe copiar los datos.

El mismo `marshal_context` se puede usar para varias conversiones de datos. Reutilizar el contexto de esta manera no afectará a los resultados de las llamadas de cálculo de referencias anteriores.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Construye un objeto `marshal_context` que se va a utilizar para la conversión de datos entre tipos de datos administrados y nativos.|
|[marshal_context::~marshal_context](#tilde-marshal-context)|Destruye un objeto `marshal_context`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Realiza el cálculo de referencias en un objeto de datos concreto para convertirlo entre un tipo de datos administrado y otro nativo.|

## <a name="requirements"></a>Requisitos

**Archivo de encabezado:** \<msclr\marshal.h >, \<msclr \ marshal_windows. h >, \<msclr \ marshal_cppstd. h > o \<msclr \ marshal_atl. h >

**Espacio de nombres:** msclr:: Interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context:: marshal_context

Construye un objeto `marshal_context` que se va a utilizar para la conversión de datos entre tipos de datos administrados y nativos.

```cpp
marshal_context();
```

### <a name="remarks"></a>Observaciones

Algunas conversiones de datos requieren un contexto de cálculo de referencias. Para obtener más información acerca de las traducciones que requieren un contexto y el archivo de serialización que se debe incluir en la aplicación, vea [información general sobre el C++cálculo de referencias en ](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [marshal_context:: marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context:: ~ marshal_context

Destruye un objeto `marshal_context`.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Observaciones

Algunas conversiones de datos requieren un contexto de cálculo de referencias. Vea [información general sobre el cálculo C++ de referencias en](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de las traducciones que requieren un contexto y el archivo de serialización que debe incluirse en la aplicación.

Al eliminar un objeto de `marshal_context`, se invalidarán los datos convertidos por ese contexto. Si desea conservar los datos después de que se destruya un objeto de `marshal_context`, debe copiar manualmente los datos en una variable que se conservará.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context:: marshal_as

Realiza el cálculo de referencias en un objeto de datos concreto para convertirlo entre un tipo de datos administrado y otro nativo.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parámetros

*input*<br/>
de Valor que se desea serializar en una variable de `To_Type`.

### <a name="return-value"></a>Valor devuelto

Variable de tipo `To_Type` que es el valor convertido de `input`.

### <a name="remarks"></a>Observaciones

Esta función realiza el cálculo de referencias en un objeto de datos específico. Use esta función solo con las conversiones indicadas por la tabla en [información general sobre el cálculo C++de referencias en ](../dotnet/overview-of-marshaling-in-cpp.md).

Si intenta calcular las referencias de un par de tipos de datos que no se admiten, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación. Lea el mensaje proporcionado con el error para obtener más información. El error `C4996` se puede generar para algunas funciones, aparte de las que están en desuso. Dos condiciones que generan este error son intentar calcular las referencias de un par de tipos de datos que no se admiten e intentan usar `marshal_as` para una conversión que requiere un contexto.

La biblioteca de cálculo de referencias se compone de varios archivos de encabezado. Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones. La tabla de `Marshaling Overview in C++` indica qué archivo de serialización se debe incluir para cada conversión.

### <a name="example"></a>Ejemplo

En este ejemplo se crea un contexto para calcular las referencias de un `System::String` a un tipo de variable `const char *`. Los datos convertidos no serán válidos después de la línea que elimina el contexto.

```cpp
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
