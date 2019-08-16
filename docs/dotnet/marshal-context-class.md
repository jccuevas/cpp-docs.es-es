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
ms.openlocfilehash: 25fc2be80ba0e5d8c7f76cee1f22eed4d1bb4fc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384873"
---
# <a name="marshalcontext-class"></a>serializar_context (Clase)

Esta clase convierte datos entre los entornos nativos y administrados.

## <a name="syntax"></a>Sintaxis

```cpp
class marshal_context
```

## <a name="remarks"></a>Comentarios

Use la `marshal_context` clase para las conversiones de datos que requieren un contexto. Para obtener más información acerca de qué conversiones requieren un contexto y qué archivo de cálculo de referencias debe incluirse, consulte [información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md). El resultado del cálculo de referencias cuando se usa un contexto es válido solo hasta el `marshal_context` se destruye el objeto. Para conservar su resultado, debe copiar los datos.

El mismo `marshal_context` puede usarse para varias conversiones de datos. Volver a usar el contexto de esta manera no afectará a los resultados de las llamadas de serialización anteriores.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción| 
|---------|-----------| 
|[marshal_context::marshal_context](#marshal-context)|Construye un `marshal_context` objeto va a usar para la conversión de datos entre los tipos de datos administrados y nativos.| 
|[marshal_context::~marshal_context](#tilde-marshal-context)|Destruye un objeto `marshal_context`.| 

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción| 
|---------|-----------| 
|[marshal_context::marshal_as](#marshal-as)|Realiza el cálculo de referencias en un objeto de datos específicos para convertirla entre administrado y un tipo de datos nativos.| 


## <a name="requirements"></a>Requisitos

**Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\marshal_windows. h >, \<msclr\marshal_cppstd. h >, o \<msclr\marshal_atl. h >

**Namespace:** msclr:: Interop

## <a name="marshal-context"></a>marshal_context::marshal_context

Construye un `marshal_context` objeto va a usar para la conversión de datos entre los tipos de datos administrados y nativos.

```cpp
marshal_context();
```

### <a name="remarks"></a>Comentarios

Algunas conversiones de datos requieren un contexto de cálculo de referencias. Para obtener más información sobre qué traducciones requieren un contexto y el cálculo de referencias de archivo que se debe incluir en la aplicación, consulte [información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [serializar_context:: serializar_as](../dotnet/marshal-context-marshal-as.md).


## <a name="tilde-marshal-context"></a>marshal_context::~marshal_context

Destruye un objeto `marshal_context`.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Comentarios

Algunas conversiones de datos requieren un contexto de cálculo de referencias. Consulte [información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de qué traducciones requieren un contexto y qué archivo de cálculo de referencias debe incluirse en la aplicación.

Eliminar un `marshal_context` objeto invalidará los datos convertidos por ese contexto. Si desea conservar los datos después de un `marshal_context` se destruye el objeto, debe copiar manualmente los datos a una variable que se conservará.

## <a name="marshal-as"></a>marshal_context::marshal_as

Realiza el cálculo de referencias en un objeto de datos específicos para convertirla entre administrado y un tipo de datos nativos.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parámetros

*input*<br/>
[in] El valor que se desea calcular las referencias a un `To_Type` variable.

### <a name="return-value"></a>Valor devuelto

Una variable de tipo `To_Type` que es el valor convertido de `input`.

### <a name="remarks"></a>Comentarios

Esta función realiza el cálculo de referencias en un objeto de datos específico. Utilice esta función sólo con las conversiones indicadas por la tabla de [información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md).

Si se intenta serializar un par de tipos de datos que no se admiten, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación. Lea el mensaje proporcionado con el error para obtener más información. El error `C4996` se puede generar para algunas funciones, aparte de las que están en desuso. Dos de las condiciones que generan este error se intenta serializar un par de tipos de datos que no son compatibles e intentar usar `marshal_as` para una conversión que requiere un contexto.

La biblioteca de cálculo de referencias se compone de varios archivos de encabezado. Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones. La tabla de `Marshaling Overview in C++` indica qué archivo de cálculo de referencias debe incluirse en cada conversión.

### <a name="example"></a>Ejemplo

Este ejemplo crea un contexto de cálculo de referencias desde un `System::String` a un `const char *` tipo de variable. Los datos convertidos no sean válidos después de la línea que elimina el contexto.

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