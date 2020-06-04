---
title: Platform::Object (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 8300ec484bdb58919ce8e450b706dd07c275ceee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363683"
---
# <a name="platformobject-class"></a>Platform::Object (Clase)

Proporciona un comportamiento común para las clases ref y los structs ref en las aplicaciones de Windows en tiempo de ejecución. Todas las instancias de clase ref y struct ref se pueden convertir implícitamente a Platform::Object^ y pueden invalidar su método ToString virtual.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class Object : Object
```

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Object::Object](#ctor)|Inicializa una nueva instancia de la clase Object.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Object::Equals](#equals)|Determina si el objeto especificado es igual que el objeto actual.|
|[Object::GetHashCode](#gethashcode)|Devuelve el código hash para esta instancia.|
|[Object::ReferenceEquals](#referenceequals)|Determina si las instancias de Object especificadas son la misma instancia.|
|[ToString](#tostring)|Devuelve una cadena que representa el objeto actual. Puede invalidarse.|
|[GetType](#gettype)|Obtiene un [Platform::Type](../cppcx/platform-type-class.md) que describe la instancia actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Object`

`Object`

### <a name="requirements"></a>Requisitos

**Encabezado:** vccorlib.h

**Espacio de nombres:** Platform

## <a name="objectequals-method"></a><a name="equals"></a>Object::Equals Método

Determina si el objeto especificado es igual que el objeto actual.

### <a name="syntax"></a>Sintaxis

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si los objetos son iguales, de lo contrario **false**.

## <a name="objectgethashcode-method"></a><a name="gethashcode"></a>Object::GetHashCode Método

Devuelve el valor de identidad `IUnknown`* para esta instancia si es un objeto COM o un valor hash calculado si no es un objeto COM.

### <a name="syntax"></a>Sintaxis

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valor devuelto

Valor numérico que identifica de forma única este objeto.

### <a name="remarks"></a>Observaciones

Puedes usar GetHashCode para crear claves para objetos de mapas. Puede comparar códigos hash mediante [Object::Equals](#equals). Si la ruta de acceso del código es sumamente crítica y `GetHashCode` y `Equals` no son suficientemente rápidos, puedes bajar hasta el nivel COM subyacente y realizar comparaciones de puntero de `IUnknown` nativo.

## <a name="objectgettype-method"></a><a name="gettype"></a>Object::GetType Método

Devuelve un [objeto Platform::Type](../cppcx/platform-type-class.md) que describe el tipo de tiempo de ejecución de un objeto.

### <a name="syntax"></a>Sintaxis

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un objeto [Platform::Type](../cppcx/platform-type-class.md) que describe el tipo de tiempo de ejecución del objeto.

### <a name="remarks"></a>Observaciones

El estático [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) se puede utilizar para obtener un [Platform::TypeCode enumeration](../cppcx/platform-typecode-enumeration.md) valor que representa el tipo actual. Esto es especialmente útil para los tipos integrados. El código de tipo para cualquier clase ref además de [Platform::String](../cppcx/platform-string-class.md) es Object (1).

La clase [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) se utiliza en las API de Windows como una forma independiente del lenguaje de pasar información de tipo entre los componentes y las aplicaciones de Windows. La clase T[Platform::Type](../cppcx/platform-type-class.md) tiene `Type` operadores para convertir entre y `TypeName`.

Usa el operador [typeid](../extensions/typeid-cpp-component-extensions.md) para devolver un `Platform::Type` objeto para un nombre de clase, por ejemplo, al navegar entre páginas XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="objectobject-constructor"></a><a name="ctor"></a>Objeto::Constructor de objetos

Inicializa una nueva instancia de la clase Object.

### <a name="syntax"></a>Sintaxis

```cpp
public:Object();
```

## <a name="objectreferenceequals-method"></a><a name="referenceequals"></a>Object::ReferenceEquals Método

Determina si las instancias de Object especificadas son la misma instancia.

### <a name="syntax"></a>Sintaxis

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parámetros

*obj1*<br/>
Primer objeto que se va a comparar.

*obj2*<br/>
Segundo objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si los dos objetos son iguales; de lo contrario, **false**.

## <a name="objecttostring-method-ccx"></a><a name="tostring"></a>Object::ToString (Método) (C++/CX)

Devuelve una cadena que representa el objeto actual.

### <a name="syntax"></a>Sintaxis

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Valor devuelto

Cadena que representa el objeto actual. Puedes invalidar este método para proporcionar un mensaje de cadena personalizado en la clase o el struct ref:

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)<br/>
[Platform::Type (Clase)](platform-type-class.md)<br/>
[Sistema de tipos](type-system-c-cx.md)
