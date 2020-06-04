---
title: Platform::Type (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 7463a2518e6ec5cc84f59db05cfaf60e43eb9fde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322091"
---
# <a name="platformtype-class"></a>Platform::Type (Clase)

Contiene información en tiempo de ejecución sobre un tipo, en concreto, un nombre de cadena y un typecode. Se obtiene llamando a [Object::GetType](../cppcx/platform-object-class.md#gettype) en cualquier objeto o utilizando el operador [typeid](../extensions/typeid-cpp-component-extensions.md) en un nombre de clase o estructura.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Observaciones

La clase `Type` es útil en aplicaciones que deben dirigir el procesamiento mediante una instrucción `if` o `switch` que se bifurca en función del tipo en tiempo de ejecución de un objeto. El código de tipo que describe la categoría de un tipo se recupera mediante el [Type::GetTypeCode](#gettypecode) función miembro.

## <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|[método Type::GetTypeCode](#gettypecode)|Devuelve un valor de [enumeración Platform::TypeCode](../cppcx/platform-typecode-enumeration.md) para el objeto.|
|[Type::ToString Método](#tostring)|Devuelve el nombre del tipo tal como se especifica en sus metadatos.|

## <a name="public-properties"></a>Propiedades públicas

|||
|-|-|
|[Tipo::FullName](#fullname)|Devuelve una [clase Platform::String](../cppcx/platform-string-class.md)^ que representa el nombre completo del tipo y usa . (punto) como separador, no :: (doble colon), por ejemplo, `MyNamespace.MyClass`.|

## <a name="conversion-operators"></a>Operadores de conversión

|||
|-|-|
|[Tipo de operador](../cppcx/operator-type-hat.md)|Permite la conversión de `Windows::UI::Xaml::Interop::TypeName` a `Platform::Type`.|
|[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Permite la conversión de `Platform::Type` a `Windows::UI::Xaml::Interop::TypeName`.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo soportado:** Windows 8

**Servidor mínimo soportado:** Windows Server 2012

**Espacio de nombres:** Platform

**Metadatos:** platform.winmd

## <a name="typefullname-property"></a><a name="fullname"></a>Type::FullName (Propiedad)

Recupera el nombre completo del tipo actual `Namespace.Type`en el formulario .

### <a name="syntax"></a>Sintaxis

```cpp
String^ FullName();
```

### <a name="return-value"></a>Valor devuelto

El nombre del tipo.

### <a name="example"></a>Ejemplo

```cpp
//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>Type::GetTypeCode Método

Recupera una categoría de tipo numérico de tipos integrados.

### <a name="syntax"></a>Sintaxis

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Valor devuelto

Uno de los valores enumerados de Platform::TypeCode.

### <a name="remarks"></a>Observaciones

El equivalente del método miembro GetTypeCode() es la propiedad `typeid`.

## <a name="typetostring-method"></a><a name="tostring"></a>Type::ToString Método

Recupera un nombre del tipo.

### <a name="syntax"></a>Sintaxis

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Valor devuelto

Un nombre del tipo tal como se especifica en sus metadatos.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
