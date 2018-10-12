---
title: 'Clase Platform:: String | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d9c68bde9fdd49e4007b8b6e1d92899d71dde4e
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162547"
---
# <a name="platformstring-class"></a>Platform::String (Clase)

Representa una cadena es una colección secuencial de caracteres Unicode que se utiliza para representar texto. Para obtener más información y ejemplos, vea [cadenas](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Sintaxis

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterators

Dos funciones de iterador, que no son miembros de la clase String, se pueden utilizar con la función de plantilla de `std::for_each` para enumerar los caracteres de un objeto String.

|Miembro|Descripción|
|------------|-----------------|
|`const char16* begin(String^ s)`|Devuelve un puntero al principio del objeto String especificado.|
|`const char16* end(String^ s)`|Devuelve un puntero después del final del objeto String especificado.|

### <a name="members"></a>Miembros

La clase String hereda de Object y las interfaces IDisposable, IEquatable e IPrintable.

La clase String también tiene los siguientes tipos de miembros.

**Constructores**

|Miembro|Descripción|
|------------|-----------------|
|[String](#ctor)|Inicializa una nueva instancia de la clase String.|

**Métodos**

La clase String hereda los métodos Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() y ToString() de [Platform::Object Class](../cppcx/platform-object-class.md). String también tiene los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[String](#begin)|Devuelve un puntero al principio de la cadena actual.|
|[String::CompareOrdinal](#compareordinal)|Compara dos objetos `String` mediante la evaluación de los valores numéricos de los caracteres correspondientes en los dos valores alfanuméricos representados por los objetos.|
|[String:: Concat](#concat)|Concatena los valores de dos objetos String.|
|[String](#data)|Devuelve un puntero al principio de la cadena actual.|
|[Dispose](#dispose)|Libera recursos.|
|[String](#end)|Devuelve un puntero después del final de la cadena actual.|
|[Equals](#equals)|Indica si el objeto especificado es igual al objeto actual.|
|[String::GetHashCode](#gethashcode)|Devuelve el código hash de esta instancia.|
|[IsEmpty](#isempty)|Indica si el objeto String actual está vacío.|
|[Isfastpass](#isfastpass)|Indica si el objeto String actual participa en un *pase rápido* operación. En una operación rápida de paso, se suspende el recuento de referencias.|
|[Length](#length)|Recupera la longitud del objeto String actual.|
|[String::ToString](#tostring)|Devuelve un objeto String cuyo valor es igual al de la cadena actual.|

**Operadores**

La clase String tiene los siguientes operadores.

|Miembro|Descripción|
|------------|-----------------|
|[String:: operator == (operador)](#operator-equality)|Indica si dos objetos String especificados tienen el mismo valor.|
|[operator+ (Operador)](#operator-plus)|Concatena dos objetos String en un nuevo objeto String.|
|[String:: operator > (operador)](#operator-greater-than)|Indica si el valor de un objeto String es mayor que el valor de un segundo objeto String.|
|[String:: operator > = (operador)](#operator-greater-than-or-equals)|Indica si el valor de un objeto String es mayor o igual que el valor de un segundo objeto String.|
|[String:: operator! = (operador)](#operator-inequality)|Indica si dos objetos String especificados tienen valores diferentes.|
|[String:: operator < (operador)](#operator-less-than)|Indica si el valor de un objeto String es menor que el valor de un segundo objeto String.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Encabezado** vccorlib.h (incluido de forma predeterminada)

## <a name="begin"></a>  String (método)

Devuelve un puntero al principio de la cadena actual.

### <a name="syntax"></a>Sintaxis

```cpp
char16* Begin();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de la cadena actual.

## <a name="compareordinal"></a>  CompareOrdinal (método)

Compara dos objetos `String` mediante la evaluación de los valores numéricos de los caracteres correspondientes en los dos valores alfanuméricos representados por los objetos.

### <a name="syntax"></a>Sintaxis

```cpp
int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer objeto String.

*str2*<br/>
El segundo objeto String.

### <a name="return-value"></a>Valor devuelto

Entero que indica la relación léxica que existe entre los dos términos de una comparación. La tabla siguiente muestra los valores devueltos posibles.

|Valor|Condición|
|-----------|---------------|
|-1|`str1` es menor que `str2`.|
|0|`str1` es igual que `str2`.|
|1|`str1` es mayor que `str2`.|

## <a name="concat"></a>  Concat (método)

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

## <a name="data"></a>  String (método)

Devuelve un puntero al principio del búfer de datos del objeto como una matriz de estilo C de elementos `char16` (`wchar_t`).

### <a name="syntax"></a>Sintaxis

```
const char16* Data();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de un `const char16` matriz de caracteres Unicode (`char16` es un typedef para `wchar_t`).

### <a name="remarks"></a>Comentarios

Usa este método para convertir de `Platform::String^` a `wchar_t*`. Cuando el objeto `String` sale del ámbito, ya no se garantiza que el puntero a datos sea válido. Para almacenar los datos más allá de la duración del original `String` de objeto, utilice [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) para copiar la matriz en la memoria que has asignado.

## <a name="dispose"></a>  Dispose (método)

Libera recursos.

### <a name="syntax"></a>Sintaxis

```cpp
virtual override void Dispose();
```

## <a name="end"></a>  String (método)

Devuelve un puntero después del final de la cadena actual.

### <a name="syntax"></a>Sintaxis

```cpp
char16* End();
```

### <a name="return-value"></a>Valor devuelto

Un puntero después del final de la cadena actual.

### <a name="remarks"></a>Comentarios

End() devuelve Begin() + Length.

## <a name="equals"></a>  Equals (método)

Indica si el objeto String especificado tiene el mismo valor que el objeto actual.

### <a name="syntax"></a>Sintaxis

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si `str` es igual al objeto actual; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Este método es equivalente a la [CompareOrdinal](#compareordinal). En la primera sobrecarga, se espera que el parámetro `str` se pueda convertir en un objeto String^.

## <a name="gethashcode"></a>  GetHashCode (método)

Devuelve el código hash de esta instancia.

### <a name="syntax"></a>Sintaxis

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Valor devuelto

Código hash de esta instancia.

## <a name="isempty"></a>  IsEmpty (método)

Indica si el objeto String actual está vacío.

### <a name="syntax"></a>Sintaxis

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Valor devuelto

**True** si actual `String` objeto es **null** o una cadena vacía (L""); en caso contrario, **false**.

## <a name="isfastpass"></a>  Isfastpass (método)

Indica si el objeto String actual participa en un *pase rápido* operación. En una operación rápida de paso, se suspende el recuento de referencias.

### <a name="syntax"></a>Sintaxis

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Valor devuelto

**True** si actual `String` objeto es paso rápido; de lo contrario, **false**.

### <a name="remarks"></a>Comentarios

En una llamada a una función donde un objeto con recuento de referencias es un parámetro y la función llamada solo lee ese objeto, el compilador puede suspender de forma segura el recuento de referencias y mejorar el rendimiento de la llamada. El código no puede hacer nada útil con esta propiedad. El sistema controla todos los detalles.

## <a name="length"></a>  Length (método)

Recupera el número de caracteres actual `String` objeto.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Valor devuelto

El número de caracteres actual `String` objeto.

### <a name="remarks"></a>Comentarios

La longitud de un objeto String sin caracteres es cero. La longitud de la cadena siguiente es 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

La matriz de caracteres devuelta por la [String](#data) tiene un carácter adicional, que es NULL de terminación o '\0'. Este carácter tiene también dos bytes de longitud.

## <a name="operator-plus"></a>  String:: operator + (operador)

Concatena dos [cadena](../cppcx/platform-string-class.md) objetos en un nuevo [cadena](../cppcx/platform-string-class.md) objeto.

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

**True** si *str1* es igual a *str2*; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Este operador crea un objeto `String^` que contiene los datos de los operandos. Úsalo por comodidad cuando no sea necesario un rendimiento extreme. Es probable que algunas llamadas a "`+`" en una función no produzcan efectos apreciables, pero si estás manipulando objetos grandes o datos de texto en un bucle ajustado, usa los mecanismos y los tipos estándar de C++.

##  <a name="operator-equality"></a> String:: operator == (operador)

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

**True** si el contenido de `str1` son iguales a `str2`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Este operador es equivalente a [CompareOrdinal](#compareordinal).

##  <a name="operator-greater-than"></a>  String:: operator&gt;

Indica si el valor de uno `String` objeto es mayor que el valor de un segundo `String` objeto.

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

**True** si el valor de `str1` es mayor que el valor de `str2`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Este operador es equivalente a llamar explícitamente a [CompareOrdinal](#compareordinal) y obtener un resultado mayor que cero.

## <a name="operator-greater-than-or-equals"></a> String:: operator&gt;=

Indica si el valor de uno `String` objeto es mayor o igual que el valor de un segundo `String` objeto.

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

**True** si el valor de `str1` es mayor o igual que el valor de `str2`; en caso contrario, **false**.

## <a name="operator-inequality"></a> String:: operator! =

Indica si dos especificada `String` objetos tienen valores diferentes.

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

**True** si `str1` no es igual a `str2`; en caso contrario, **false**.

## <a name="operator-less-than"></a> String:: operator&lt;

Indica si el valor de uno `String` objeto es menor que el valor de un segundo `String` objeto.

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

**True** si el valor de *str1* es menor que el valor de *str2*; en caso contrario, **false**.

## <a name="ctor"></a> Constructor de String

Inicializa una nueva instancia de la `String` clase con una copia de los datos de cadena de entrada.

### <a name="syntax"></a>Sintaxis

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parámetros

*s*<br/>
Serie de caracteres anchos que inicializan la cadena. char16

*n*<br/>
Un número que especifica la longitud de la cadena.

### <a name="remarks"></a>Comentarios

Si el rendimiento es crítico y controlar la duración de la cadena de origen, puede usar [stringreference](../cppcx/platform-stringreference-class.md) en lugar de cadena.
### <a name="example"></a>Ejemplo

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a> ToString

Devuelve un `String` objeto cuyo valor es igual que la cadena actual.

### <a name="syntax"></a>Sintaxis

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Valor devuelto

Un `String` objeto cuyo valor es igual que la cadena actual.

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)