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
ms.openlocfilehash: 77313f8c4dcc87fa9de852afe2d60e614f8fc3a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423673"
---
# <a name="platformobject-class"></a>Platform::Object (Clase)

Proporciona un comportamiento común para clases Ref y Structs Ref en Windows Runtime aplicaciones. Todas las instancias de clase ref y struct ref se pueden convertir implícitamente a Platform::Object^ y pueden invalidar su método ToString virtual.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class Object : Object
```

### <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Objeto:: Object](#ctor)|Inicializa una nueva instancia de la clase Object.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Object:: Equals](#equals)|Determina si el objeto especificado es igual que el objeto actual.|
|[Objeto:: GetHashCode](#gethashcode)|Devuelve el código hash para esta instancia.|
|[Objeto:: ReferenceEquals](#referenceequals)|Determina si las instancias de Object especificadas son la misma instancia.|
|[ToString](#tostring)|Devuelve una cadena que representa el objeto actual. Puede invalidarse.|
|[GetType](#gettype)|Obtiene un [Platform::Type](../cppcx/platform-type-class.md) que describe la instancia actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Object`

`Object`

### <a name="requirements"></a>Requisitos

**Encabezado:** vccorlib.h

**Espacio de nombres:** Plataforma

## <a name="equals"></a>Object:: Equals (método)

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

**true** si los objetos son iguales; de lo contrario, **false**.

## <a name="gethashcode"></a>Object:: GetHashCode (método)

Devuelve el valor de identidad `IUnknown`* para esta instancia si es un objeto COM o un valor hash calculado si no es un objeto COM.

### <a name="syntax"></a>Sintaxis

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valor devuelto

Valor numérico que identifica de forma única este objeto.

### <a name="remarks"></a>Observaciones

Puedes usar GetHashCode para crear claves para objetos de mapas. Puede comparar códigos hash mediante [Object:: Equals](#equals). Si la ruta de acceso del código es sumamente crítica y `GetHashCode` y `Equals` no son suficientemente rápidos, puedes bajar hasta el nivel COM subyacente y realizar comparaciones de puntero de `IUnknown` nativo.

## <a name="gettype"></a>Object:: GetType (método)

Devuelve un objeto [Platform:: Type](../cppcx/platform-type-class.md) que describe el tipo en tiempo de ejecución de un objeto.

### <a name="syntax"></a>Sintaxis

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Objeto [Platform:: Type](../cppcx/platform-type-class.md) que describe el tipo en tiempo de ejecución del objeto.

### <a name="remarks"></a>Observaciones

El [tipo estático:: GetTypeCode](../cppcx/platform-type-class.md#gettypecode) se puede usar para obtener un valor de [enumeración Platform:: TypeCode](../cppcx/platform-typecode-enumeration.md) que representa el tipo actual. Esto es especialmente útil para los tipos integrados. El código de tipo de cualquier clase Ref además de [Platform:: String](../cppcx/platform-string-class.md) es Object (1).

La clase [Windows:: UI:: XAML:: Interop:: TypeName](/uwp/api/windows.ui.xaml.interop.typename) se usa en las API de Windows como una manera independiente del lenguaje de pasar información de tipos entre los componentes y aplicaciones de Windows. La[clase T Platform:: Type](../cppcx/platform-type-class.md) tiene operadores para la conversión entre `Type` y `TypeName`.

Use el operador [typeid](../extensions/typeid-cpp-component-extensions.md) para devolver un `Platform::Type` objeto para un nombre de clase, por ejemplo, al navegar entre las páginas XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>Object:: Object (constructor)

Inicializa una nueva instancia de la clase Object.

### <a name="syntax"></a>Sintaxis

```cpp
public:Object();
```

## <a name="referenceequals"></a>Object:: ReferenceEquals (método)

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

**true** si los dos objetos son iguales; en caso contrario, **false**.

## <a name="tostring"></a>Object:: ToString (métodoC++) (/CX)

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
