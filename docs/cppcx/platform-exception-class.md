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
ms.openlocfilehash: 4604769d9d1bc5fa848d15459327dc87d82f7016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363781"
---
# <a name="platformexception-class"></a>Platform::Exception (Clase)

Representa los errores que se producen durante la ejecución de la aplicación. Las clases de excepción personalizadas no se pueden derivar de `Platform::Exception`. Si necesitas una excepción personalizada, puedes utilizar `Platform::COMException` y especificar un HRESULT específico de la aplicación.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Miembros

La clase `Exception` hereda de la clase `Object` y las interfaces `IException`, `IPrintable`y `IEquatable` .

La clase `Exception` también tiene las siguientes clases de miembros.

### <a name="constructors"></a>Constructores

|Member|Descripción|
|------------|-----------------|
|[Excepción::Excepción](#ctor)|Inicializa una nueva instancia de la clase `Exception`.|

### <a name="methods"></a>Métodos

La clase `Exception` hereda los métodos `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`y `ToString()` de [Platform::Object Class](../cppcx/platform-object-class.md). La clase `Exception` también tiene el método siguiente.

|Member|Descripción|
|------------|-----------------|
|[Excepción::CreateException](#createexception)|Crea una excepción que representa el valor HRESULT especificado.|

### <a name="properties"></a>Propiedades

La clase Exception también tiene las propiedades siguientes.

|Member|Descripción|
|------------|-----------------|
|[Excepción::HResult](#hresult)|HRESULT correspondiente a la excepción.|
|[Excepción::Mensaje](#message)|Mensaje que describe la excepción. Este valor es de solo lectura y se no puede modificarse después de que se haya generado `Exception` .|

### <a name="requirements"></a>Requisitos

**Cliente mínimo soportado:** Windows 8

**Servidor mínimo soportado:** Windows Server 2012

**Espacio de nombres:** Platform

**Metadatos:** platform.winmd

## <a name="exceptioncreateexception-method"></a><a name="createexception"></a>Exception::CreateException Método

Crea una excepción Platform::Exception^ a partir de un valor HRESULT especificado.

### <a name="syntax"></a>Sintaxis

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>Parámetros

*Hr*<br/>
Un valor HRESULT que se obtiene normalmente de una llamada a un método COM. Si el valor es 0, que es igual a S_OK, este método produce [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) porque los métodos COM que se realizan correctamente no deben producir excepciones.

*Mensaje*<br/>
Cadena que describe el error.

### <a name="return-value"></a>Valor devuelto

Una excepción que representa el HRESULT de error.

### <a name="remarks"></a>Observaciones

Utiliza este método para crear una excepción a partir de un valor HRESULT devuelto, por ejemplo, desde una llamada a un método de interfaz COM. Puedes utilizar la sobrecarga que toma un parámetro String^ para proporcionar un mensaje personalizado.

Se recomienda encarecidamente usar CreateException para crear una excepción fuertemente tipada en lugar de crear una [excepción Platform::COMException](../cppcx/platform-comexception-class.md) que simplemente contenga el Valor HRESULT.

## <a name="exceptionexception-constructor"></a><a name="ctor"></a>Excepción::Exception Constructor

Inicializa una nueva instancia de la clase Exception.

### <a name="syntax"></a>Sintaxis

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>Parámetros

*Hresult*<br/>
Valor HRESULT de error representado por la excepción.

*Mensaje*<br/>
Mensaje especificado por el usuario, como texto preceptivo, asociado a la excepción. Normalmente, deberías optar por la segunda sobrecarga para proporcionar un mensaje descriptivo que sea lo más específico posible sobre cómo y por qué se ha producido el error.

## <a name="exceptionhresult-property"></a><a name="hresult"></a>Exception::HResult (Propiedad)

HRESULT correspondiente a la excepción.

### <a name="syntax"></a>Sintaxis

```cpp
public:
    property int HResult { int get(); }
```

## <a name="property-value"></a>Valor de la propiedad

Valor HRESULT.

### <a name="remarks"></a>Observaciones

La mayoría de las excepciones comienzan como errores COM, que se devuelven como valores HRESULT. C++/CX convierte estos valores en objetos Platform::Exception^ y esta propiedad almacena el valor del código de error original.

## <a name="exceptionmessage-property"></a><a name="message"></a>Excepción::Propiedad Message

Mensaje que describe el error.

### <a name="syntax"></a>Sintaxis

```cpp
public:property String^ Message;
```

## <a name="property-value"></a>Valor de la propiedad

En las excepciones que se originan en Windows en tiempo de ejecución, es una descripción del error proporcionada por el sistema.

### <a name="remarks"></a>Observaciones

En Windows 8, esta propiedad es de solo lectura porque las excepciones de esa versión de Windows Runtime se transportan a través de la ABI solo como HRESULTS. En Windows 8.1, se transmite información de excepción más completa a través de la ABI y puedes proporcionar un mensaje personalizado al que otros componentes podrán tener acceso mediante programación. Para obtener más información, consulte [Excepciones (C++/CX)](../cppcx/exceptions-c-cx.md).

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
