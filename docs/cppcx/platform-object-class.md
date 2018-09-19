---
title: 'Clase Platform:: Object | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
dev_langs:
- C++
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82f9cf473a1b38e3a77b43bc5fde30057c7b1a8a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106553"
---
# <a name="platformobject-class"></a>Platform::Object (Clase)

Proporciona un comportamiento común para clases ref y structs ref en aplicaciones de Windows en tiempo de ejecución. Todas las instancias de clase ref y struct ref se pueden convertir implícitamente a Platform::Object^ y pueden invalidar su método ToString virtual.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class Object : Object
```

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Object](#ctor)|Inicializa una nueva instancia de la clase Object.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Equals](#equals)|Determina si el objeto especificado es igual al objeto actual.|
|[Object::GetHashCode](#gethashcode)|Devuelve el código hash de esta instancia.|
|[ReferenceEquals](#referenceequals)|Determina si las instancias de Object especificadas son la misma instancia.|
|[ToString](#tostring)|Devuelve una cadena que representa el objeto actual. Puede invalidarse.|
|[GetType](#gettype)|Obtiene un [Platform::Type](../cppcx/platform-type-class.md) que describe la instancia actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Object`

`Object`

### <a name="requirements"></a>Requisitos

**Encabezado:** vccorlib.h

**Espacio de nombres:** Plataforma

## <a name="equals"></a> Equals (método)

Determina si el objeto especificado es igual al objeto actual.

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

Es`true` si los objetos son iguales; de lo contrario, es `false`.

## <a name="gethashcode"></a>  GetHashCode (método)

Devuelve el valor de identidad `IUnknown`* para esta instancia si es un objeto COM o un valor hash calculado si no es un objeto COM.

### <a name="syntax"></a>Sintaxis

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valor devuelto

Valor numérico que identifica de forma única este objeto.

### <a name="remarks"></a>Comentarios

Puedes usar GetHashCode para crear claves para objetos de mapas. Puede comparar códigos hash mediante [Equals](#equals). Si la ruta de acceso del código es sumamente crítica y `GetHashCode` y `Equals` no son suficientemente rápidos, puedes bajar hasta el nivel COM subyacente y realizar comparaciones de puntero de `IUnknown` nativo.

## <a name="gettype"></a>  GetType (método)

Devuelve un [Platform:: Type](../cppcx/platform-type-class.md) objeto que describe el tipo en tiempo de ejecución de un objeto.

### <a name="syntax"></a>Sintaxis

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un [Platform:: Type](../cppcx/platform-type-class.md) objeto que describe el tipo en tiempo de ejecución del objeto.

### <a name="remarks"></a>Comentarios

Estático [Type:: GetTypeCode](../cppcx/platform-type-class.md#gettypecode) puede usarse para obtener un [TypeCode (enumeración)](../cppcx/platform-typecode-enumeration.md) valor que representa el tipo actual. Esto es especialmente útil para los tipos integrados. El código de tipo para cualquier clase ref además [Platform:: String](../cppcx/platform-string-class.md) es objeto (1).

El [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) clase se utiliza en las API de Windows como una manera independiente del lenguaje de pasar información de tipos entre los componentes de Windows y aplicaciones. La T[Platform:: Type Class](../cppcx/platform-type-class.md) tiene operadores para la conversión entre `Type` y `TypeName`.

Use la [typeid](../windows/typeid-cpp-component-extensions.md) operador para devolver un `Platform::Type` objeto para un nombre de clase, por ejemplo, al navegar entre páginas XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="see-also"></a>Vea también

[Platform::Type (Clase)](../cppcx/platform-type-class.md)<br/>
[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)<br/>
[Tipo System] (.. /cppcx/Type-System-c-CX.MD

## <a name="ctor"></a>  Constructor de Object

Inicializa una nueva instancia de la clase Object.

### <a name="syntax"></a>Sintaxis

```cpp
public:Object();
```

## <a name="referenceequals"></a>  ReferenceEquals (método)

Determina si las instancias de Object especificadas son la misma instancia.

### <a name="syntax"></a>Sintaxis

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parámetros

*Obj1*<br/>
Primer objeto que se va a comparar.

*obj2*<br/>
Segundo objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

`true` si los dos objetos son iguales; de lo contrario, `false`.

## <a name="tostring"></a>  Object:: ToString (método) (C++ / c++ / CX)

Devuelve una cadena que representa el objeto actual.

### <a name="syntax"></a>Sintaxis

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Valor devuelto

Una cadena que representa el objeto actual. Puedes invalidar este método para proporcionar un mensaje de cadena personalizado en la clase o el struct ref:

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
## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)