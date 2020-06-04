---
title: Platform::WriteOnlyArray (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
ms.openlocfilehash: d06ed19b7c041f9ae73f862ba521449a206aa321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374639"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray (Clase)

Representa una matriz unidimensional que se utiliza como parámetro de entrada cuando el llamador pasa una matriz para el método que se va a rellenar.

Esta clase ref se declara como privada en vccorlib.h; por consiguiente, no se emite en los metadatos y solo se puede usar desde C++. Esta clase está diseñada únicamente para su uso como un parámetro de entrada que recibe una matriz que el llamador ha asignado. No se puede crear desde el código de usuario. Permite a un método de C++ escribir directamente en dicha matriz, patrón que se conoce como *FillArray* . Para obtener más información, vea [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Sintaxis

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Estos métodos tienen accesibilidad interna, es decir, solo están accesibles desde la aplicación o componente de C++.

|Nombre|Descripción|
|----------|-----------------|
|[WriteOnlyArray::begin](#begin)|Un iterador que apunta al primer elemento de la matriz.|
|[WriteOnlyArray::Data](#data)|Puntero al búfer de datos.|
|[WriteOnlyArray::end](#end)|Un iterador que apunta a uno más allá del último elemento de la matriz.|
|[WriteOnlyArray::FastPass](#fastpass)|Indica si la matriz puede usar el mecanismo FastPass, que es una optimización realizada por el sistema de manera transparente. No utilices esto en tu código|
|[WriteOnlyArray::Longitud](#length)|Devuelve el número de elementos de la matriz.|
|[WriteOnlyArray::set](#set)|Establece el elemento especificado en el valor indicado.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WriteOnlyArray`

### <a name="requirements"></a>Requisitos

Opción del compilador: **/ZW**

**Metadatos:** Platform.winmd

**Espacio de nombres:** Platform

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a>WriteOnlyArray::begin Método

Devuelve un puntero al primer elemento de la matriz.

### <a name="syntax"></a>Sintaxis

```cpp
T* begin() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al primer elemento de la matriz.

### <a name="remarks"></a>Observaciones

Este iterador se puede usar con los algoritmos de STL como `std::sort` para operar en elementos de la matriz.

## <a name="writeonlyarraydata-property"></a><a name="data"></a>Propiedad WriteOnlyArray::Data

Puntero al búfer de datos.

### <a name="syntax"></a>Sintaxis

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Valor devuelto

Puntero a los bytes sin formato de la matriz.

## <a name="writeonlyarrayend-method"></a><a name="end"></a>WriteOnlyArray::end Método

Devuelve un puntero a uno más allá del último elemento de la matriz.

### <a name="syntax"></a>Sintaxis

```cpp
T* end() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador de puntero a uno más allá del último elemento de la matriz.

### <a name="remarks"></a>Observaciones

Este iterador se puede usar con los algoritmos de STL para realizar operaciones como `std::sort` en elementos de la matriz.

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a>Propiedad WriteOnlyArray::FastPass

Indica si se puede realizar la optimización interna de FastPass. No se ha diseñado para el uso en el código del usuario.

### <a name="syntax"></a>Sintaxis

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Valor devuelto

Valor booleano que indica si la matriz es FastPass.

## <a name="writeonlyarrayget-method"></a><a name="get"></a>WriteOnlyArray::get Método

Devuelve el elemento que se encuentra en el índice especificado.

### <a name="syntax"></a>Sintaxis

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Parámetros

*indexArg*<br/>
El índice que se va a utilizar.

### <a name="return-value"></a>Valor devuelto

## <a name="writeonlyarraylength-property"></a><a name="length"></a>Propiedad WriteOnlyArray::Length

Devuelve el número de elementos de la matriz asignada por el llamador.

### <a name="syntax"></a>Sintaxis

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la matriz.

## <a name="writeonlyarrayset-function"></a><a name="set"></a>Función WriteOnlyArray::set

Establece el valor especificado en el índice especificado de la matriz.

### <a name="syntax"></a>Sintaxis

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>Parámetros

*indexArg*<br/>
Índice del elemento que se va a establecer.

*valueArg*<br/>
El valor que se va a establecer en `indexArg`.

### <a name="return-value"></a>Valor devuelto

Una referencia al elemento que se acaba de establecer.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo interpretar el valor HRESULT, vea [Estructura de códigos de error COM](/windows/win32/com/structure-of-com-error-codes).

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)<br/>
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
