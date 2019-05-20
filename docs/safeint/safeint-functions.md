---
title: SafeInt (Funciones)
ms.date: 10/22/2018
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
ms.openlocfilehash: e31cf35c903a0e7572ce7d47ada21c4603119cb2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515580"
---
# <a name="safeint-functions"></a>SafeInt (Funciones)

La biblioteca SafeInt proporciona varias funciones que puede usar sin crear una instancia de la [clase SafeInt](../safeint/safeint-class.md). Si desea proteger una sola operación matemática del desbordamiento de enteros, puede usar estas funciones. Si desea proteger varias operaciones matemáticas, debe crear objetos `SafeInt`. Resulta más eficaz crear objetos `SafeInt` que usar estas funciones varias veces.

Estas funciones le permiten comparar o realizar operaciones matemáticas con dos tipos de parámetros diferentes sin tener que convertirlos en el mismo tipo primero.

Cada una de estas funciones tiene dos tipos de plantilla: `T` y `U`. Cada uno de estos tipos puede ser un valor booleano, un carácter o un tipo entero. Los tipos enteros pueden tener o no signo y cualquier tamaño entre 8 y 64 bits.

> [!NOTE]
> La versión más reciente de esta biblioteca se encuentra en [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt).

## <a name="in-this-section"></a>En esta sección

Función                      | Descripción
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Agrega dos números y protege contra el desbordamiento.
[SafeCast](#safecast)         | Convierte un tipo de parámetro en otro tipo.
[SafeDivide](#safedivide)     | Divide dos números y protege contra la división entre cero.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [SafeNotEquals](#safenotequals) | Compara dos números. Estas funciones le permiten comparar dos tipos de números diferentes sin cambiar sus tipos.
[SafeModulus](#safemodulus)   | Realiza la operación de módulo con dos números.
[SafeMultiply](#safemultiply) | Multiplica dos números y protege contra el desbordamiento.
[SafeSubtract](#safesubtract) | Resta dos números y protege contra el desbordamiento.

## <a name="related-sections"></a>Secciones relacionadas

Sección                                                  | Descripción
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../safeint/safeint-class.md)                   | La clase `SafeInt`.
[SafeIntException](../safeint/safeintexception-class.md) | Clase de excepción específica de la librería SafeInt.

## <a name="safeadd"></a>SafeAdd

Agrega dos números de una forma que protege contra el desbordamiento.

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
[in] Primer número que se va a agregar. Este debe ser del tipo T.

*u*<br/>
[in] Segundo número que se va a agregar. Este debe ser del tipo U.

*result*<br/>
[out] Parámetro donde `SafeAdd` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

**true** si no se produce ningún error; **false** si se produce un error.

## <a name="safecast"></a>SafeCast

Convierte un tipo de número en otro tipo.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parámetros

*From*<br/>
[in] Número de origen que se va a convertir. Debe ser del tipo `T`.

*En*<br/>
[out] Referencia al nuevo tipo de número. Debe ser del tipo `U`.

### <a name="return-value"></a>Valor devuelto

**true** si no se produce ningún error; **false** si se produce un error.

## <a name="safedivide"></a>SafeDivide

Divide dos números de una forma que protege contra la división entre cero.

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
[in] Divisor. Este debe ser del tipo T.

*u*<br/>
[in] Dividendo. Este debe ser del tipo U.

*result*<br/>
[out] Parámetro donde `SafeDivide` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

**true** si no se produce ningún error; **false** si se produce un error.

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
[in] Primer número que se va a comparar. Este debe ser del tipo T.

*u*<br/>
[in] Segundo número que se va a comparar. Este debe ser del tipo U.

### <a name="return-value"></a>Valor devuelto

**true** si *t* y *u* son iguales; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

El método mejora `==` porque `SafeEquals` le permite comparar dos tipos de números diferentes.

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
[in] Primer número que se va a comparar. Debe ser del tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Debe ser del tipo `U`.

### <a name="return-value"></a>Valor devuelto

**true** si *t* es mayor que *u*; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

`SafeGreaterThan` extiende el operador de comparación regular permitiéndole comparar dos tipos de números diferentes.

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
[in] Primer número que se va a comparar. Debe ser del tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Debe ser del tipo `U`.

### <a name="return-value"></a>Valor devuelto

**true** si *t* es mayor o igual que *u*; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

`SafeGreaterThanEquals` mejora el operador de comparación estándar porque le permite comparar dos tipos de números diferentes.

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
[in] Primer número. Debe ser del tipo `T`.

*u*<br/>
[in] Segundo número. Debe ser del tipo `U`.

### <a name="return-value"></a>Valor devuelto

**true** si *t* es menor que *u*; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Este método mejora el operador de comparación estándar porque `SafeLessThan` le permite comparar dos tipos de números diferentes.

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
[in] Primer número que se va a comparar. Debe ser del tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Debe ser del tipo `U`.

### <a name="return-value"></a>Valor devuelto

**true** si *t* es menor o igual que *u*; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

`SafeLessThanEquals` extiende el operador de comparación regular permitiéndole comparar dos tipos de números diferentes.

## <a name="safemodulus"></a>SafeModulus

Realiza la operación de módulo con dos números.

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
[in] Divisor. Debe ser del tipo `T`.

*u*<br/>
[in] Dividendo. Debe ser del tipo `U`.

*result*<br/>
[out] Parámetro donde `SafeModulus` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

**true** si no se produce ningún error; **false** si se produce un error.

## <a name="safemultiply"></a>SafeMultiply

Multiplica dos números de una forma que protege contra el desbordamiento.

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
[in] Primer número que se va a multiplicar. Debe ser del tipo `T`.

*u*<br/>
[in] Segundo número que se va a multiplicar. Debe ser del tipo `U`.

*result*<br/>
[out] Parámetro donde `SafeMultiply` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

`true` si no se produce ningún error; `false` si se produce un error.

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
[in] Primer número que se va a comparar. Debe ser del tipo `T`.

*u*<br/>
[in] Segundo número que se va a comparar. Debe ser del tipo `U`.

### <a name="return-value"></a>Valor devuelto

**true** si *t* y *u* no son iguales; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

El método mejora `!=` porque `SafeNotEquals` le permite comparar dos tipos de números diferentes.

## <a name="safesubtract"></a>SafeSubtract

Resta dos números de una forma que protege contra el desbordamiento.

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
[in] Primer número de la resta. Debe ser del tipo `T`.

*u*<br/>
[in] Número que se va a restar de *t*. Debe ser del tipo `U`.

*result*<br/>
[out] Parámetro donde `SafeSubtract` almacena el resultado.

### <a name="return-value"></a>Valor devuelto

**true** si no se produce ningún error; **false** si se produce un error.
