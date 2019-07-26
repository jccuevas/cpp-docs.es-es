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
ms.openlocfilehash: 60ced1f60c811f585928f47c6cfd5e695d0c4085
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457753"
---
# <a name="filestatus-class"></a>file_status (Clase)

Ajusta un [file_type](../standard-library/filesystem-enumerations.md#file_type) y los [perms](../standard-library/filesystem-enumerations.md#perms) del archivo.

## <a name="syntax"></a>Sintaxis

```cpp
class file_status;
```

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[file_status](#file_status)|Construye un contenedor para [File_Type](../standard-library/filesystem-enumerations.md#file_type) y el archivo [perms](../standard-library/filesystem-enumerations.md#perms).|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[type](#type)|Obtiene o establece el `file_type`.|
|[permissions](#permissions)|Obtiene o establece los permisos de archivo.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator=](#op_as)|Los operadores predeterminados de asignación de miembros se comportan según lo previsto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> filesystem

**Espacio de nombres:** STD:: experimental:: filesystem, STD:: experimental:: filesystem

## <a name="file_status"></a> file_status::file_status

Construye un contenedor para [File_Type](../standard-library/filesystem-enumerations.md#file_type) y el archivo [perms](../standard-library/filesystem-enumerations.md#perms).

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>Parámetros

*ftype*\
`file_type` Se`file_type::none`especifica, el valor predeterminado es.

*máscara*\
Archivo `perms`especificado, el valor predeterminado `perms::unknown`es.

*file_status*\
Objeto almacenado.

## <a name="op_as"></a> file_status::operator=

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Parámetros

*file_status*\
[File_status](../standard-library/file-status-class.md) que se va a copiar `file_status`en.

## <a name="type"></a>automáticamente

Obtiene o establece el `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Parámetros

*ftype*\
Especificado `file_type`.

## <a name="permissions"></a>los

Obtiene o establece los permisos de archivo.

Use el establecedor para crear un `readonly` archivo o quitar `readonly` el atributo.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Parámetros

*máscara*\
Especificado `perms`.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Path (clase)](../standard-library/path-class.md)\
[\<filesystem>](../standard-library/filesystem.md)
