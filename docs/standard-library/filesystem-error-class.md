---
title: Clase filesystem_error
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: c3dbfc080f0a1494950016f42189d932be05b0f1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240744"
---
# <a name="filesystemerror-class"></a>Clase filesystem_error

Una base para todas las excepciones que se producen para notificar un desbordamiento de sistema de bajo nivel.

## <a name="syntax"></a>Sintaxis

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Comentarios

Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de las funciones \<filesystem>. Almacena un objeto de tipo `string`, llamado `mymesg` aquí a efectos de la exposición. También almacena dos objetos de tipo `path`, llamado `mypval1` y `mypval2`.

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

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error

El primer constructor crea su propio mensaje de *what_arg* y *CE*. El segundo constructor también crea su propio mensaje de *pval1*, que se almacena en `mypval1`. El tercer constructor también crea su propio mensaje de *pval1*, que se almacena en `mypval1`y desde *pval2*, que se almacena en `mypval2`.

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

*CE*\
Código de error especificado.

*mypval1*\
Aún más el parámetro de mensaje especificado.

*mypval2*\
Aún más el parámetro de mensaje especificado.

## <a name="path1"></a> path1

La función miembro devuelve `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> path2

La función miembro devuelve `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> Qué

La función miembro devuelve un puntero a un `NTBS`, preferiblemente componerse de `runtime_error::what()`, `system_error::what()`, `mymesg`, `mypval1.native_string()`, y `mypval2.native_string()`.

```cpp
const char *what() const noexcept;
```
