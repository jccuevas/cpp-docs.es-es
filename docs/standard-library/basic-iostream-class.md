---
title: basic_iostream (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
dev_langs:
- C++
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 662c4915753cc49534fa9f489eb61504907744c4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954713"
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

*strbuf* existente `basic_streambuf` objeto.

*derecha* existente `basic_iostream` objeto que se usa para crear un nuevo `basic_iostream`.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa los objetos base por medio de `basic_istream(strbuf)` y `basic_ostream(strbuf)`.

El segundo constructor inicializa los objetos base llamando `move(right)`.

## <a name="op_eq"></a>  basic_iostream::operator=

Asigne el valor de un objeto `basic_iostream` especificado a este objeto. Se trata de una asignación de movimiento que implica un valor R que no deja ninguna copia atrás.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parámetros

*derecha* una `rvalue` hacen referencia a un `basic_iostream` objeto que se va a asignar desde.

### <a name="remarks"></a>Comentarios

El operador miembro llama a `swap(right)`.

## <a name="swap"></a>  basic_iostream::swap

Intercambia el contenido del objeto `basic_iostream` proporcionado con el contenido de este objeto.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parámetros

*derecha* el `basic_iostream` objeto que se intercambia.

### <a name="remarks"></a>Comentarios

La función miembro llama a `swap(right)`.

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
