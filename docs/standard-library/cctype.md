---
title: '&lt;cctype&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cctype>
helpviewer_keywords:
- cctype header
ms.assetid: 3fd18bfd-c414-4def-bac1-c362e1fe8b71
ms.openlocfilehash: 19431d02e0742d63df058ca743fc0560131805bd
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244949"
---
# <a name="ltcctypegt"></a>&lt;cctype&gt;

Incluye el encabezado \<ctype.h> de la biblioteca estándar de C y agrega los nombres asociados al espacio de nombres `std`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cctype >

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Incluir este encabezado también garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar de C se declaran en el espacio de nombres `std`.

## <a name="functions"></a>Funciones

```cpp
int isalnum(int c);
int isalpha(int c);
int isblank(int c);
int iscntrl(int c);
int isdigit(int c);
int isgraph(int c);
int islower(int c);
int isprint(int c);
int ispunct(int c);
int isspace(int c);
int isupper(int c);
int isxdigit(int c);
int tolower(int c);
int toupper(int c);
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
