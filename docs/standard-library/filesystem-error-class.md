---
title: filesystem_error (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
dev_langs:
- C++
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5756c01969dba0773e0327e1a34a0c7492b972a
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691528"
---
# <a name="filesystemerror-class"></a>filesystem_error (Clase)

Una base para todas las excepciones que se producen para notificar un desbordamiento de sistema de bajo nivel.

## <a name="syntax"></a>Sintaxis

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Comentarios

Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de las funciones \<filesystem>. Almacena un objeto de tipo `string`, llamado `mymesg` aquí a efectos de la exposición. También almacena dos objetos de tipo `path`, llamado `mypval1` y `mypval2`.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[filesystem_error](#filesystem_error)|Construye un `filesystem_error` mensaje.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[path1](#path1)|Devuelve `mypval1`|
|[path2](#path2)|Devuelve `mypval2`|
|[Qué](#what)|Devuelve un puntero a un objeto `NTBS`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error:: filesystem_error

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

*what_arg*<br/>
Mensaje especificado.

*CE*<br/>
Código de error especificado.

*mypval1*<br/>
Aún más el parámetro de mensaje especificado.

*mypval2*<br/>
Aún más el parámetro de mensaje especificado.

## <a name="path1"></a> filesystem_error:: path1

La función miembro devuelve `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> filesystem_error:: path2

La función miembro devuelve `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> filesystem_error::What

La función miembro devuelve un puntero a un `NTBS`, preferiblemente componerse de `runtime_error::what()`, `system_error::what()`, `mymesg`, `mypval1.native_string()`, y `mypval2.native_string()`.

```cpp
const char *what() const noexcept;
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[system_error (Clase)](../standard-library/system-error-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
