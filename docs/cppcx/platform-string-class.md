---
title: Platform::String (Clase)
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: 3f29c60d0d6a4618d97d8f750a048fcc18f976b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322113"
---
# <a name="platformstring-class"></a>Platform::String (Clase)

Representa una cadena es una colección secuencial de caracteres Unicode que se utiliza para representar texto. Para obtener más información y ejemplos, consulte [Cadenas](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Sintaxis

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterators

Dos funciones de iterador, que no son miembros de la clase String, se pueden utilizar con la función de plantilla de `std::for_each` para enumerar los caracteres de un objeto String.

|Member|Descripción|
|------------|-----------------|
|`const char16* begin(String^ s)`|Devuelve un puntero al principio del objeto String especificado.|
|`const char16* end(String^ s)`|Devuelve un puntero después del final del objeto String especificado.|

## <a name="members"></a>Miembros

La clase String hereda de Object y las interfaces IDisposable, IEquatable e IPrintable.

La clase String también tiene los siguientes tipos de miembros.

### <a name="constructors"></a>Constructores

|Member|Descripción|
|------------|-----------------|
|[String::String](#ctor)|Inicializa una nueva instancia de la clase String.|

### <a name="methods"></a>Métodos

La clase String hereda los métodos Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() y ToString() de [Platform::Object Class](../cppcx/platform-object-class.md). String también tiene los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[String::Begin](#begin)|Devuelve un puntero al principio de la cadena actual.|
|[String::CompareOrdinal](#compareordinal)|Compara dos objetos `String` mediante la evaluación de los valores numéricos de los caracteres correspondientes en los dos valores alfanuméricos representados por los objetos.|
|[String::Concat](#concat)|Concatena los valores de dos objetos String.|
|[String::Data](#data)|Devuelve un puntero al principio de la cadena actual.|
|[String::Dispose](#dispose)|Libera recursos.|
|[String::Fin](#end)|Devuelve un puntero después del final de la cadena actual.|
|[String::Equals](#equals)|Indica si el objeto especificado es igual al objeto actual.|
|[String::GetHashCode](#gethashcode)|Devuelve el código hash para esta instancia.|
|[String::IsEmpty](#isempty)|Indica si el objeto String actual está vacío.|
|[String::IsFastPass](#isfastpass)|Indica si el objeto String actual participa en una operación de *paso rápido.* En una operación rápida de paso, se suspende el recuento de referencias.|
|[Cadena::Longitud](#length)|Recupera la longitud del objeto String actual.|
|[String::ToString](#tostring)|Devuelve un objeto String cuyo valor es igual al de la cadena actual.|

### <a name="operators"></a>Operadores

La clase String tiene los siguientes operadores.

|Member|Descripción|
|------------|-----------------|
|[Cadena::operador- Operador](#operator-equality)|Indica si dos objetos String especificados tienen el mismo valor.|
|[operator+ (Operador)](#operator-plus)|Concatena dos objetos String en un nuevo objeto String.|
|[Operador de cadena::operador>](#operator-greater-than)|Indica si el valor de un objeto String es mayor que el valor de un segundo objeto String.|
|[String::operator>- Operador](#operator-greater-than-or-equals)|Indica si el valor de un objeto String es mayor o igual que el valor de un segundo objeto String.|
|[Cadena::operador!- Operador](#operator-inequality)|Indica si dos objetos String especificados tienen valores diferentes.|
|[Operador de cadena::operador<](#operator-less-than)|Indica si el valor de un objeto String es menor que el valor de un segundo objeto String.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo soportado:** Windows 8

**Servidor mínimo soportado:** Windows Server 2012

**Espacio de nombres:** Platform

**Encabezado** vccorlib.h (incluido de forma predeterminada)

## <a name="stringbegin-method"></a><a name="begin"></a>String::Begin Método

Devuelve un puntero al principio de la cadena actual.

### <a name="syntax"></a>Sintaxis

```cpp
char16* Begin();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de la cadena actual.

## <a name="stringcompareordinal-method"></a><a name="compareordinal"></a>String::CompareOrdinal Método

Método estático que `String` compara dos objetos mediante la evaluación de los valores numéricos de los caracteres correspondientes en los dos valores de cadena representados por los objetos.

### <a name="syntax"></a>Sintaxis

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer objeto String.

*str2*<br/>
El segundo objeto String.

### <a name="return-value"></a>Valor devuelto

Entero que indica la relación léxica que existe entre los dos términos de una comparación. La tabla siguiente muestra los valores devueltos posibles.

|Value|Condición|
|-----------|---------------|
|-1|`str1` es menor que `str2`.|
|0|`str1` es igual que `str2`.|
|1|`str1` es mayor que `str2`.|

## <a name="stringconcat-method"></a><a name="concat"></a>String::Concat Método

Concatena los valores de dos objetos String.

### <a name="syntax"></a>Sintaxis

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer objeto String o `null`.

*str2*<br/>
El segundo objeto String o `null`.

### <a name="return-value"></a>Valor devuelto

Un nuevo objeto String^ cuyo valor es la concatenación de los valores de `str1` y `str2`.

Si `str1` es `null` y `str2` no lo es, se devuelve `str1`. Si `str2` es `null` y `str1` no lo es, se devuelve `str2`. Si `str1` y `str2` son ambos `null`, se devuelve la cadena vacía (L"").

## <a name="stringdata-method"></a><a name="data"></a>String::Data Método

Devuelve un puntero al principio del búfer de datos del objeto como una matriz de estilo C de elementos `char16` (`wchar_t`).

### <a name="syntax"></a>Sintaxis

```cpp
const char16* Data();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio `const char16` de una`char16` matriz de caracteres `wchar_t`Unicode ( es una conversión de tipos para ).

### <a name="remarks"></a>Observaciones

Usa este método para convertir de `Platform::String^` a `wchar_t*`. Cuando el objeto `String` sale del ámbito, ya no se garantiza que el puntero a datos sea válido. Para almacenar los datos más `String` allá de la duración del objeto original, utilice [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) para copiar la matriz en la memoria que usted mismo ha asignado.

## <a name="stringdispose-method"></a><a name="dispose"></a>Método String::Dispose

Libera recursos.

### <a name="syntax"></a>Sintaxis

```cpp
virtual override void Dispose();
```

## <a name="stringend-method"></a><a name="end"></a>String::End Método

Devuelve un puntero después del final de la cadena actual.

### <a name="syntax"></a>Sintaxis

```cpp
char16* End();
```

### <a name="return-value"></a>Valor devuelto

Un puntero después del final de la cadena actual.

### <a name="remarks"></a>Observaciones

End() devuelve Begin() + Length.

## <a name="stringequals-method"></a><a name="equals"></a>String::Equals Método

Indica si el objeto String especificado tiene el mismo valor que el objeto actual.

### <a name="syntax"></a>Sintaxis

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** `str` si es igual al objeto actual; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Este método es equivalente a la [estática String::CompareOrdinal](#compareordinal). En la primera sobrecarga, se espera que el parámetro `str` se pueda convertir en un objeto String^.

## <a name="stringgethashcode-method"></a><a name="gethashcode"></a>String::GetHashCode Método

Devuelve el código hash para esta instancia.

### <a name="syntax"></a>Sintaxis

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Valor devuelto

Código hash de esta instancia.

## <a name="stringisempty-method"></a><a name="isempty"></a>String::IsEmpty Método

Indica si el objeto String actual está vacío.

### <a name="syntax"></a>Sintaxis

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Valor devuelto

**true** si `String` el objeto actual es **null** o la cadena vacía (L""); de lo contrario, **false**.

## <a name="stringisfastpass-method"></a><a name="isfastpass"></a>String::IsFastPass Método

Indica si el objeto String actual participa en una operación de *paso rápido.* En una operación rápida de paso, se suspende el recuento de referencias.

### <a name="syntax"></a>Sintaxis

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Valor devuelto

**true** si `String` el objeto actual es de pasado rápido; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

En una llamada a una función donde un objeto con recuento de referencias es un parámetro y la función llamada solo lee ese objeto, el compilador puede suspender de forma segura el recuento de referencias y mejorar el rendimiento de la llamada. El código no puede hacer nada útil con esta propiedad. El sistema controla todos los detalles.

## <a name="stringlength-method"></a><a name="length"></a>String::Método de longitud

Recupera el número de caracteres del objeto actual. `String`

### <a name="syntax"></a>Sintaxis

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Valor devuelto

El número de caracteres del objeto actual. `String`

### <a name="remarks"></a>Observaciones

La longitud de un objeto String sin caracteres es cero. La longitud de la cadena siguiente es 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

La matriz de caracteres devuelta por el [String::Data](#data) tiene un carácter adicional, que es la terminación de NULL o '-0'. Este carácter tiene también dos bytes de longitud.

## <a name="stringoperator-operator"></a><a name="operator-plus"></a>Cadena::operador+ Operador

Concatena dos [String](../cppcx/platform-string-class.md) objetos en un nuevo [String](../cppcx/platform-string-class.md) objeto.

### <a name="syntax"></a>Sintaxis

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer objeto `String`.

*str2*<br/>
Segundo objeto `String`, cuyo contenido se anexará a `str1`.

### <a name="return-value"></a>Valor devuelto

**true** si *str1* es igual a *str2*; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Este operador crea un objeto `String^` que contiene los datos de los operandos. Úsalo por comodidad cuando no sea necesario un rendimiento extreme. Es probable que algunas llamadas a "`+`" en una función no produzcan efectos apreciables, pero si estás manipulando objetos grandes o datos de texto en un bucle ajustado, usa los mecanismos y los tipos estándar de C++.

## <a name="stringoperator-operator"></a><a name="operator-equality"></a>Cadena::operador- Operador

Indica si dos objetos String especificados tienen el mismo valor de texto.

### <a name="syntax"></a>Sintaxis

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
Primer objeto `String` que se va a comparar.

*str2*<br/>
Segundo objeto `String` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el `str1` contenido `str2`de es igual a ; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Este operador es equivalente a [String::CompareOrdinal](#compareordinal).

## <a name="stringoperatorgt"></a><a name="operator-greater-than"></a>String::operator&gt;

Indica si el valor `String` de un objeto es `String` mayor que el valor de un segundo objeto.

### <a name="syntax"></a>Sintaxis

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer objeto `String`.

*str2*<br/>
Segundo objeto `String`.

### <a name="return-value"></a>Valor devuelto

**true** si el `str1` valor de es `str2`mayor que el valor de ; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Este operador equivale a llamar explícitamente [a String::CompareOrdinal](#compareordinal) y obtener un resultado mayor que cero.

## <a name="stringoperatorgt"></a><a name="operator-greater-than-or-equals"></a>String::operator&gt;=

Indica si el valor `String` de un objeto es mayor o `String` igual que el valor de un segundo objeto.

### <a name="syntax"></a>Sintaxis

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer objeto `String`.

*str2*<br/>
Segundo objeto `String`.

### <a name="return-value"></a>Valor devuelto

**true** si el `str1` valor de es mayor `str2`o igual que el valor de ; de lo contrario, **false**.

## <a name="stringoperator"></a><a name="operator-inequality"></a>Cadena::operador!

Indica si dos `String` objetos especificados tienen valores diferentes.

### <a name="syntax"></a>Sintaxis

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
Primer objeto `String` que se va a comparar.

*str2*<br/>
Segundo objeto `String` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** `str1` si no `str2`es igual a ; de lo contrario, **false**.

## <a name="stringoperatorlt"></a><a name="operator-less-than"></a>String::operator&lt;

Indica si el valor `String` de un objeto es `String` menor que el valor de un segundo objeto.

### <a name="syntax"></a>Sintaxis

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer objeto `String`.

*str2*<br/>
Segundo objeto `String`.

### <a name="return-value"></a>Valor devuelto

**true** si el valor de *str1* es menor que el valor de *str2*; de lo contrario, **false**.

## <a name="stringstring-constructor"></a><a name="ctor"></a>String::String Constructor

Inicializa una nueva instancia `String` de la clase con una copia de los datos de cadena de entrada.

### <a name="syntax"></a>Sintaxis

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parámetros

*s*<br/>
Serie de caracteres anchos que inicializan la cadena. char16

*N*<br/>
Un número que especifica la longitud de la cadena.

### <a name="remarks"></a>Observaciones

Si el rendimiento es crítico y controla la duración de la cadena de origen, puede usar [Platform::StringReference](../cppcx/platform-stringreference-class.md) en lugar de String.

### <a name="example"></a>Ejemplo

```cpp
String^ s = L"Hello!";
```

## <a name="stringtostring"></a><a name="tostring"></a>String::ToString

Devuelve `String` un objeto cuyo valor es el mismo que la cadena actual.

### <a name="syntax"></a>Sintaxis

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Valor devuelto

Objeto `String` cuyo valor es el mismo que la cadena actual.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
