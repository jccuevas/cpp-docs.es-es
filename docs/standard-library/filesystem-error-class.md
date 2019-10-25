---
title: Clase filesystem_error
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 7bd6b2d3d716ba25999388d44e7bd5a8d0750eb5
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127201"
---
# <a name="filesystem_error-class"></a>Clase filesystem_error

Una base para todas las excepciones que se producen para notificar un desbordamiento de sistema de bajo nivel.

## <a name="syntax"></a>Sintaxis

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Comentarios

Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de las funciones \<filesystem>. Almacena un objeto de tipo `string`, al que se llama `mymesg` aquí para la exposición. También almacena dos objetos de tipo `path`, denominados `mypval1` y. `mypval2`

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[filesystem_error](#filesystem_error)|Construye un `filesystem_error` mensaje.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[path1](#path1)|Devuelve `mypval1`|
|[path2](#path2)|Devuelve `mypval2`|
|[what](#what)|Devuelve un puntero a un objeto `NTBS`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> filesystem

**Espacio de nombres:** std::experimental::filesystem

## <a name="filesystem_error"></a>filesystem_error

El primer constructor crea su mensaje de *what_arg* y *EC*. El segundo constructor también crea su mensaje a partir de *pval1*, que almacena en `mypval1`. El tercer constructor también crea su mensaje a partir de *pval1*, que almacena en `mypval1`y desde *pval2*, que almacena en `mypval2`.

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>Parámetros

*what_arg*\
Mensaje especificado.

*n°*\
Código de error especificado.

*mypval1*\
Parámetro de mensaje especificado.

*mypval2*\
Parámetro de mensaje especificado.

## <a name="path1"></a>ruta1

La función miembro devuelve `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a>rutaDeAcceso2

La función miembro devuelve `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a>elemento

La función miembro devuelve un puntero a un `NTBS`, preferiblemente creado a `runtime_error::what()`partir `system_error::what()`de `mymesg`, `mypval1.native_string()`,, `mypval2.native_string()`y.

```cpp
const char *what() const noexcept;
```
