---
title: filesystem_error (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e1acf34f8478bc075b53780f1e48df125c22608b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845497"
---
# <a name="filesystemerror-class"></a>filesystem_error (Clase)

Una base para todas las excepciones que se producen para notificar un desbordamiento de sistema de bajo nivel.

## <a name="syntax"></a>Sintaxis

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Comentarios

Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de las funciones \<filesystem>. Almacena un objeto de tipo string, denominado mymesg aquí a efectos de la exposición. También almacena dos objetos de tipo path, denominados mypval1 y mypval2.

## <a name="filesystemerrorfilesystemerror"></a>filesystem_error::filesystem_error

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

El primer constructor crea su propio mensaje a partir de what_arg y ec. El segundo constructor también crea su propio mensaje a partir de pval1 y lo almacena en mypval1. El tercer constructor también crea su propio mensaje a partir de pval1, que almacena en mypval1, y a partir de pval2, que almacena en mypval2.

## <a name="filesystemerrorpath1"></a>filesystem_error::path1

```cpp
const path& path1() const noexcept;
```

La función miembro devuelve mypval1.

## <a name="filesystemerrorpath2"></a>filesystem_error::path2

```cpp
const path& path2() const noexcept;
```

La función miembro devuelve mypval2.

## <a name="filesystemerrorwhat"></a>filesystem_error::what

```cpp
const char *what() const noexcept;
```

La función miembro devuelve un puntero a un NTBS, preferiblemente creado a partir de runtime_error::what(), system_error::what(), mymesg, mypval1.native_string() y mypval2.native_string().

## <a name="requirements"></a>Requisitos

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::experimental::filesystem

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[system_error (Clase)](../standard-library/system-error-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
