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
ms.openlocfilehash: 110fe4abf7eb90b05e7feef563efa4882bed0fc6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332010"
---
# <a name="marshal_context-class"></a>serializar_context (Clase)

Esta clase convierte datos entre entornos nativos y administrados.

## <a name="syntax"></a>Sintaxis

```cpp
class marshal_context
```

## <a name="remarks"></a>Observaciones

Utilice `marshal_context` la clase para las conversiones de datos que requieren un contexto. Para obtener más información sobre qué conversiones requieren un contexto y qué archivo de cálculo de referencias debe incluirse, consulte [Información general sobre el cálculo de referencias en C++](../dotnet/overview-of-marshaling-in-cpp.md). El resultado del cálculo de referencias cuando se `marshal_context` utiliza un contexto solo es válido hasta que se destruye el objeto. Para conservar el resultado, debe copiar los datos.

Lo `marshal_context` mismo se puede utilizar para numerosas conversiones de datos. La reutilización del contexto de esta manera no afectará a los resultados de las llamadas de cálculo de referencias anteriores.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Construye un `marshal_context` objeto que se usará para la conversión de datos entre tipos de datos administrados y nativos.|
|[marshal_context::marshal_context](#tilde-marshal-context)|Destruye un objeto `marshal_context` .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Realiza el cálculo de referencias en un objeto de datos específico para convertirlo entre un tipo de datos administrado y un tipo de datos nativo.|

## <a name="requirements"></a>Requisitos

Archivo de **encabezado:** \<msclr-marshal.h \<>, msclr-marshal_windows.h>, \<msclr-marshal_cppstd.h> o \<msclr-marshal_atl.h>

**Espacio de nombres:** msclr::interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context::marshal_context

Construye un `marshal_context` objeto que se usará para la conversión de datos entre tipos de datos administrados y nativos.

```cpp
marshal_context();
```

### <a name="remarks"></a>Observaciones

Algunas conversiones de datos requieren un contexto de cálculo de referencias. Para obtener más información acerca de qué traducciones requieren un contexto y qué archivo de cálculo de referencias debe incluir en la aplicación, consulte [Información general sobre el cálculo de referencias en C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo [de marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context::marshal_context

Destruye un objeto `marshal_context` .

```cpp
~marshal_context();
```

### <a name="remarks"></a>Observaciones

Algunas conversiones de datos requieren un contexto de cálculo de referencias. Consulte Información general sobre el [cálculo de referencias en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información sobre qué traducciones requieren un contexto y qué archivo de cálculo de referencias debe incluirse en la aplicación.

La eliminación `marshal_context` de un objeto invalidará los datos convertidos por ese contexto. Si desea conservar los datos `marshal_context` después de destruir un objeto, debe copiar manualmente los datos en una variable que persistirá.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context::marshal_as

Realiza el cálculo de referencias en un objeto de datos específico para convertirlo entre un tipo de datos administrado y un tipo de datos nativo.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parámetros

*input*<br/>
[en] El valor que desea calcular `To_Type` las referencias a una variable.

### <a name="return-value"></a>Valor devuelto

Variable de `To_Type` tipo que es el `input`valor convertido de .

### <a name="remarks"></a>Observaciones

Esta función realiza el cálculo de referencias en un objeto de datos específico. Utilice esta función solo con las conversiones indicadas por la tabla en [Visión general del cálculo de referencias en C++.](../dotnet/overview-of-marshaling-in-cpp.md)

Si intenta calcular las referencias de un par `marshal_as` de tipos de datos que no se admiten, generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación. Lea el mensaje proporcionado con el error para obtener más información. El error `C4996` se puede generar para algunas funciones, aparte de las que están en desuso. Dos condiciones que generan este error son intentar calcular las referencias de `marshal_as` un par de tipos de datos que no se admiten y cómo intentar usar para una conversión que requiere un contexto.

La biblioteca de cálculo de referencias se compone de varios archivos de encabezado. Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones. La tabla `Marshaling Overview in C++` en indica qué archivo de cálculo de referencias debe incluirse para cada conversión.

### <a name="example"></a>Ejemplo

En este ejemplo se crea `System::String` un `const char *` contexto para el cálculo de referencias de un tipo de variable a a. Los datos convertidos no serán válidos después de la línea que elimina el contexto.

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
