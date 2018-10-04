---
title: SafeInt (funciones) | Microsoft Docs
ms.custom: ''
ms.date: 09/28/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
dev_langs:
- C++
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 504cfe0780cfb0116f59ae67937ea5f0370dc8b2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235573"
---
# <a name="safeint-functions"></a>SafeInt (Funciones)

La Biblioteca SafeInt proporciona varias funciones que puede utilizar sin necesidad de crear una instancia de la [clase SafeInt](../windows/safeint-class.md). Si desea proteger una sola operación matemática de desbordamiento de enteros, puede usar estas funciones. Si desea proteger varias operaciones matemáticas, debe crear `SafeInt` objetos. Resulta más eficaz crear `SafeInt` objetos para usar estas funciones varias veces.

Estas funciones permiten comparar o realizar operaciones matemáticas con dos tipos diferentes de parámetros sin tener que convertir en primer lugar en el mismo tipo.

Cada una de estas funciones tiene dos tipos de plantilla: `T` y `U`. Cada uno de estos tipos puede ser un valor booleano, un carácter o un tipo entero. Tipos enteros pueden ser con o sin signo y de cualquier tamaño de 8 bits a 64 bits.

## <a name="in-this-section"></a>En esta sección

Función                      | Descripción
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Suma dos números y protege contra el desbordamiento.
[SafeCast](#safecast)         | Convierte un tipo de parámetro a otro tipo.
[SafeDivide](#safedivide)     | Divide dos números y protege frente al dividir por cero.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [ SafeNotEquals](#safenotequals) | Compara dos números. Estas funciones le permiten comparar dos tipos diferentes de números sin cambiar sus tipos.
[SafeModulus](#safemodulus)   | Realiza la operación de módulo en dos números.
[SafeMultiply](#safemultiply) | Multiplica a dos números juntos y protege contra el desbordamiento.
[SafeSubtract](#safesubtract) | Resta dos números y protege contra el desbordamiento.

## <a name="related-sections"></a>Secciones relacionadas

Sección                                                  | Descripción
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../windows/safeint-class.md)                   | La clase `SafeInt`.
[SafeIntException](../windows/safeintexception-class.md) | La clase de excepción específica de la Biblioteca SafeInt.

## <a name="safeadd"></a>SafeAdd

Suma dos números de forma que protege contra el desbordamiento.

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] Primer número que se va a agregar. Debe ser de tipo T.

*u*<br/>
[in] Segundo número que se va a agregar. Debe ser de tipo U.

*Resultado*<br/>
[out] El parámetro donde `SafeAdd` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

`true` Si se produce ningún error; `false` si se produce un error.

## <a name="safecast"></a>SafeCast

Convierte un tipo de número a otro tipo.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parámetros

*From*<br/>
[in] Para convertir el número de origen. Esto debe ser de tipo `T`.

*En*<br/>
[out] Una referencia al nuevo tipo de número. Esto debe ser de tipo `U`.

### <a name="return-value"></a>Valor devuelto

`true` Si se produce ningún error; `false` si se produce un error.

## <a name="safedivide"></a>SafeDivide

Divide dos números de forma que protege frente al dividir por cero.

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El divisor. Debe ser de tipo T.

*u*<br/>
[in] El dividendo. Debe ser de tipo U.

*Resultado*<br/>
[out] El parámetro donde `SafeDivide` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

`true` Si se produce ningún error; `false` si se produce un error.

## <a name="safeequals"></a>SafeEquals

Compara dos números para determinar si son iguales.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número que se compara. Debe ser de tipo T.

*u*<br/>
[in] Segundo número que se va a comparar. Debe ser de tipo U.

### <a name="return-value"></a>Valor devuelto

`true` Si *t* y *u* son iguales; en caso contrario `false`.

### <a name="remarks"></a>Comentarios

El método mejora `==` porque `SafeEquals` permite comparar dos tipos diferentes de números.

## <a name="safegreaterthan"></a>SafeGreaterThan

Compara dos números.

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número que se compara. Esto debe ser de tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Esto debe ser de tipo `U`.

### <a name="return-value"></a>Valor devuelto

`true` Si *t* es mayor que *u*; de lo contrario `false`.

### <a name="remarks"></a>Comentarios

`SafeGreaterThan` el operador de comparación normal se extiende por lo que le permite comparar dos tipos diferentes de números.

## <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Compara dos números.

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número que se compara. Esto debe ser de tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Esto debe ser de tipo `U`.

### <a name="return-value"></a>Valor devuelto

`true` Si *t* es mayor o igual a *u*; de lo contrario `false`.

### <a name="remarks"></a>Comentarios

`SafeGreaterThanEquals` mejora el operador de comparación estándar porque permite comparar dos tipos diferentes de números.

## <a name="safelessthan"></a>SafeLessThan

Determina si un número es menor que otro.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número. Esto debe ser de tipo `T`.

*u*<br/>
[in] El segundo número. Esto debe ser de tipo `U`.

### <a name="return-value"></a>Valor devuelto

`true` Si *t* es menor que *u*; de lo contrario `false`.

### <a name="remarks"></a>Comentarios

Este método mejora, el operador de comparación estándar ya `SafeLessThan` permite comparar dos tipos diferentes de número.

## <a name="safelessthanequals"></a>SafeLessThanEquals

Compara dos números.

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número que se compara. Esto debe ser de tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Esto debe ser de tipo `U`.

### <a name="return-value"></a>Valor devuelto

`true` Si *t* es menor o igual que *u*; de lo contrario `false`.

### <a name="remarks"></a>Comentarios

`SafeLessThanEquals` el operador de comparación normal se extiende por lo que le permite comparar dos tipos diferentes de números.

## <a name="safemodulus"></a>SafeModulus

Realiza la operación de módulo en dos números.

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El divisor. Esto debe ser de tipo `T`.

*u*<br/>
[in] El dividendo. Esto debe ser de tipo `U`.

*Resultado*<br/>
[out] El parámetro donde `SafeModulus` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

`true` Si se produce ningún error; `false` si se produce un error.

## <a name="safemultiply"></a>SafeMultiply

Multiplica a dos números juntos de forma que protege contra el desbordamiento.

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número a multiplicar. Esto debe ser de tipo `T`.

*u*<br/>
[in] El segundo número a multiplicar. Esto debe ser de tipo `U`.

*Resultado*<br/>
[out] El parámetro donde `SafeMultiply` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

`true` Si se produce ningún error; `false` si se produce un error.

## <a name="safenotequals"></a>SafeNotEquals

Determina si dos números no son iguales.

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número que se compara. Esto debe ser de tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Esto debe ser de tipo `U`.

### <a name="return-value"></a>Valor devuelto

`true` Si *t* y *u* no son iguales; en caso contrario `false`.

### <a name="remarks"></a>Comentarios

El método mejora `!=` porque `SafeNotEquals` permite comparar dos tipos diferentes de números.

## <a name="safesubtract"></a>SafeSubtract

Resta dos números de forma que protege contra el desbordamiento.

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parámetros

*t*<br/>
[in] El primer número de la resta. Esto debe ser de tipo `T`.

*u*<br/>
[in] El número para restárselo a *t*. Esto debe ser de tipo `U`.

*Resultado*<br/>
[out] El parámetro donde `SafeSubtract` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

`true` Si se produce ningún error; `false` si se produce un error.
