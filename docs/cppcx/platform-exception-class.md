---
title: Platform::Exception (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
ms.openlocfilehash: 8579b3506d727f5c4faeb56a9c1f3ea88b7a4b6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464966"
---
# <a name="platformexception-class"></a>Platform::Exception (Clase)

Representa los errores que se producen durante la ejecución de una aplicación. Las clases de excepción personalizadas no se pueden derivar de `Platform::Exception`. Si necesitas una excepción personalizada, puedes utilizar `Platform::COMException` y especificar un HRESULT específico de la aplicación.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Miembros

La clase `Exception` hereda de la clase `Object` y las interfaces `IException`, `IPrintable`y `IEquatable` .

La clase `Exception` también tiene las siguientes clases de miembros.

### <a name="constructors"></a>Constructores

|Miembro|Descripción|
|------------|-----------------|
|[Exception](#ctor)|Inicializa una nueva instancia de la clase `Exception`.|

### <a name="methods"></a>Métodos

La clase `Exception` hereda los métodos `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`y `ToString()` de [Platform::Object Class](../cppcx/platform-object-class.md). La clase `Exception` también tiene el método siguiente.

|Miembro|Descripción|
|------------|-----------------|
|[Exception:: CreateException](#createexception)|Crea una excepción que representa el valor HRESULT especificado.|

### <a name="properties"></a>Propiedades

La clase Exception también tiene las propiedades siguientes.

|Miembro|Descripción|
|------------|-----------------|
|[Exception:: HRESULT](#hresult)|HRESULT correspondiente a la excepción.|
|[Exception:: Message](#message)|Un mensaje que describe la excepción. Este valor es de solo lectura y se no puede modificarse después de que se haya generado `Exception` .|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd

## <a name="createexception"></a> CreateException (método)

Crea una excepción Platform::Exception^ a partir de un valor HRESULT especificado.

### <a name="syntax"></a>Sintaxis

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>Parámetros

*recursos humanos*<br/>
Un valor HRESULT que se obtiene normalmente de una llamada a un método COM. Si el valor es 0, lo que es igual a S_OK, este método produce [Platform:: InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) porque los métodos COM que se realice correctamente no deberían producir excepciones.

*message*<br/>
Cadena que describe el error.

### <a name="return-value"></a>Valor devuelto

Una excepción que representa el HRESULT de error.

### <a name="remarks"></a>Comentarios

Utiliza este método para crear una excepción a partir de un valor HRESULT devuelto, por ejemplo, desde una llamada a un método de interfaz COM. Puedes utilizar la sobrecarga que toma un parámetro String^ para proporcionar un mensaje personalizado.

Es muy recomendable utilizar CreateException para crear una excepción fuertemente tipada en lugar de crear un [Platform:: COMException](../cppcx/platform-comexception-class.md) simplemente que contenga el valor HRESULT.

## <a name="ctor"></a>  Constructor de Exception

Inicializa una nueva instancia de la clase Exception.

### <a name="syntax"></a>Sintaxis

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>Parámetros

*HRESULT*<br/>
Valor HRESULT de error representado por la excepción.

*message*<br/>
Mensaje especificado por el usuario, como texto preceptivo, asociado a la excepción. Normalmente, deberías optar por la segunda sobrecarga para proporcionar un mensaje descriptivo que sea lo más específico posible sobre cómo y por qué se ha producido el error.

## <a name="hresult"></a>  Exception:: HRESULT Property

HRESULT correspondiente a la excepción.

### <a name="syntax"></a>Sintaxis

```cpp
public:
    property int HResult { int get(); }
```

## <a name="property-value"></a>Valor de propiedad

Valor HRESULT.

### <a name="remarks"></a>Comentarios

La mayoría de las excepciones comienzan como errores COM, que se devuelven como valores HRESULT. C++/CX convierte estos valores en objetos Platform::Exception^ y esta propiedad almacena el valor del código de error original.

## <a name="message"></a> Propiedad Exception

Mensaje que describe el error.

### <a name="syntax"></a>Sintaxis

```cpp
public:property String^ Message;
```

## <a name="property-value"></a>Valor de propiedad

En las excepciones que se originan en Windows Runtime, es una descripción del error proporcionada por el sistema.

### <a name="remarks"></a>Comentarios

En Windows 8, esta propiedad es de solo lectura porque las excepciones en esa versión de Windows Runtime se transportan a través de ABI solo como valores HRESULT. En Windows 8.1, se transmite información de excepción más completa a través de la ABI y puedes proporcionar un mensaje personalizado al que otros componentes podrán tener acceso mediante programación. Para obtener más información, consulte [excepciones (C++ / c++ / CX)](../cppcx/exceptions-c-cx.md).

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)