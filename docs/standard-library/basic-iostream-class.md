---
title: basic_iostream (Clase)
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: 80aad69f05b7473b508447d6f69f1d92edbeeca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400648"
---
# <a name="basiciostream-class"></a>basic_iostream (Clase)

Clase de secuencia que puede realizar tanto operaciones de entrada como de salida.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_iostream : public basic_istream<Elem, Tr>,
    public basic_ostream<Elem, Tr>
{
public:
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};
```

## <a name="remarks"></a>Comentarios

La clase de plantilla describe un objeto que controla las inserciones a través de su clase base [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> y las extracciones a través de su clase base [basic_istream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`>. Los dos objetos comparten una clase base virtual común [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>. También administran un búfer de secuencia común, con elementos de tipo `Elem`, cuyos rasgos de caracteres vienen determinados por la clase `Tr`. El constructor inicializa sus clases base a través de `basic_istream`(**strbuf**) and `basic_ostream`(**strbuf**).

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_iostream](#basic_iostream)|Crear un objeto `basic_iostream`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[swap](#swap)|Intercambia el contenido del objeto `basic_iostream` proporcionado con el contenido de este objeto.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna el valor de un objeto `basic_iostream` especificado a este objeto. Se trata de una asignación de movimiento que implica un `rvalue` que no deja ninguna copia atrás.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<istream>

**Espacio de nombres:** std

## <a name="basic_iostream"></a>  basic_iostream::basic_iostream

Crear un objeto `basic_iostream`.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parámetros

*strbuf*<br/>
Objeto `basic_streambuf` existente.

*right*<br/>
Objeto `basic_iostream` existente que se usa para construir un nuevo `basic_iostream`.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa los objetos base por medio de `basic_istream(strbuf)` y `basic_ostream(strbuf)`.

El segundo constructor inicializa los objetos base llamando `move(right)`.

## <a name="op_eq"></a>  basic_iostream::operator=

Asigne el valor de un objeto `basic_iostream` especificado a este objeto. Se trata de una asignación de movimiento que implica un valor R que no deja ninguna copia atrás.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Referencia `rvalue` a un objeto `basic_iostream` desde el que se va a asignar.

### <a name="remarks"></a>Comentarios

El operador miembro llama a `swap(right)`.

## <a name="swap"></a>  basic_iostream::swap

Intercambia el contenido del objeto `basic_iostream` proporcionado con el contenido de este objeto.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Objeto `basic_iostream` que se va a intercambiar.

### <a name="remarks"></a>Comentarios

La función miembro llama a `swap(right)`.

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
