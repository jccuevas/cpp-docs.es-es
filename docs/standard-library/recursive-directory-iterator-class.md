---
title: recursive_directory_iterator (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
dev_langs:
- C++
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd876ec21379d59445b88bdc08a1c7b831cb94fa
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator (Clase)

Describe un iterador de entrada que secuencia a través de los nombres de archivo de un directorio, posiblemente descendiendo a los subdirectorios de forma repetitiva. En el caso de un iterador X, la expresión *X se evalúa como un objeto de la clase directory_entry que contiene el nombre de archivo y cualquier elemento conocido sobre su estado.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Sintaxis

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena:

1. un objeto del tipo stack<pair\<directory_iterator, path>>, denominado aquí mystack a efectos de la exposición, que representa el anidamiento de directorios que se va a secuenciar

1. un objeto del tipo directory_entry denominado aquí myentry, que representa el nombre de archivo actual en la secuencia de directorio;

1. un objeto del tipo bool, denominado aquí no_push, que registra si está deshabilitado el descenso recursivo en subdirectorios;

1. un objeto del tipo directory_options, denominado aquí myoptions, que registra las opciones establecidas en la construcción.

Un objeto construido de forma predeterminada del tipo recursive_directory_entry tiene un iterador de final de secuencia en mystack.top().first y representa el iterador de fin de secuencia. Por ejemplo, si tenemos el directorio abc con las entradas def (un directorio), def/ghi y jkl, el código:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

llamará a visit con los argumentos `path("abc/def/ghi") and path("abc/jkl").`. Para calificar secuencias a través de un subárbol de un directorio puede usar dos mecanismos:

1. Un symlink de directorio se examinará solo si se construye un recursive_directory_iterator con un argumento directory_options cuyo valor es directory_options::follow_directory_symlink.

1. Si se llama a disable_recursion_pending, un directorio posterior encontrado durante un incremento no se examinará de forma recursiva.

## <a name="recursivedirectoryiteratordepth"></a>recursive_directory_iterator::depth

```cpp
int depth() const;
```

Devuelve mystack.size() - 1, por lo que pval está en una profundidad de cero.

## <a name="recursivedirectoryiteratordisablerecursionpending"></a>recursive_directory_iterator::disable_recursion_pending

```cpp
void disable_recursion_pending();
```

La función miembro almacena true en no_push.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator!=

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

El operador miembro devuelve !(*this == right).

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator=

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator==

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

El operador miembro solo devuelve true si *this y right son iteradores de final de secuencia o si ninguno de los dos lo son.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator*

```cpp
const directory_entry& operator*() const;
```

El operador miembro devuelve myentry.

## <a name="recursivedirectoryiteratoroperator-"></a>recursive_directory_iterator::operator->

```cpp
const directory_entry * operator->() const;
```

Devuelve &\*\*this.

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator++

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

La primera función miembro llama a increment() y luego devuelve *this. La segunda función miembro hace una copia del objeto, llama a increment() y luego devuelve la copia.

## <a name="recursivedirectoryiteratoroptions"></a>recursive_directory_iterator::options

```cpp
directory_options options() const;
```

Devuelve myoptions.

## <a name="recursivedirectoryiteratorpop"></a>recursive_directory_iterator::pop

```cpp
void pop();
```

Si depth() == 0, el objeto se convierte en un iterador de final de secuencia. De lo contrario, la función miembro termina el análisis del directorio actual (más profundo) y lo reanuda en el siguiente nivel inferior.

## <a name="recursivedirectoryiteratorrecursionpending"></a>recursive_directory_iterator::recursion_pending

```cpp
bool recursion_pending() const;
```

Devuelve !no_push.

## <a name="recursivedirectoryiteratorrecursivedirectoryiterator"></a>recursive_directory_iterator::recursive_directory_iterator

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

El primer constructor crea un iterador de final de secuencia. Los constructores segundo y tercero almacenan false en no_push y directory_options::none in myoptions y después, intentan abrir y leer pval como un directorio. Si es correcto, inicializan mystack y myentry para designar el primer nombre de archivo que no es de directorio en la secuencia anidada; de lo contrario producen un iterador de final de secuencia.

Los constructores cuarto y quinto se comportan igual que el segundo y el tercero, salvo que almacenan primero opts en myoptions. Los constructores predeterminados se comportan según lo previsto.

## <a name="recursivedirectoryiteratorincrement"></a>recursive_directory_iterator::increment

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

La función intenta avanzar al siguiente nombre de archivo de la secuencia anidada. Si es correcto, almacena ese nombre de archivo en myentry; en caso contrario, produce un iterador de final de secuencia.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::tr2::sys

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)<br/>
