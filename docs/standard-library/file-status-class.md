---
title: file_status (Clase)
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 81ce4ecc1673087db8e985f94e297798dd712a6e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630625"
---
# <a name="filestatus-class"></a>file_status (Clase)

Ajusta un [file_type](../standard-library/filesystem-enumerations.md#file_type) y los [perms](../standard-library/filesystem-enumerations.md#perms) del archivo.

## <a name="syntax"></a>Sintaxis

```cpp
class file_status;
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[file_status](#file_status)|Crea un contenedor para [file_type](../standard-library/filesystem-enumerations.md#file_type) y archivo [perms](../standard-library/filesystem-enumerations.md#perms).|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[type](#type)|Obtiene o establece el `file_type`.|
|[permissions](#permissions)|Obtiene o establece los permisos de archivo.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_as)|Los operadores predeterminados de asignación de miembros se comportan según lo previsto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<filesystem >

**Namespace:** std::experimental::filesystem, std::experimental::filesystem

## <a name="file_status"></a> file_status::file_status

Crea un contenedor para [file_type](../standard-library/filesystem-enumerations.md#file_type) y archivo [perms](../standard-library/filesystem-enumerations.md#perms).

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>Parámetros

*FTYPE*<br/>
Especifica `file_type`, el valor predeterminado es `file_type::none`.

*Máscara*<br/>
Archivo especificado `perms`, el valor predeterminado es `perms::unknown`.

*file_status*<br/>
El objeto almacenado.

## <a name="op_as"></a> file_status::operator =

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Parámetros

*file_status*<br/>
El [file_status](../standard-library/file-status-class.md) que se copia en el `file_status`.

## <a name="type"></a> Tipo

Obtiene o establece el `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Parámetros

*FTYPE*<br/>
Especificado `file_type`.

## <a name="permissions"></a> Permisos

Obtiene o establece los permisos de archivo.

Use el establecedor para hacer que un archivo `readonly` o quitar el `readonly` atributo.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Parámetros

*Máscara*<br/>
Especificado `perms`.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[path (Clase)](../standard-library/path-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
