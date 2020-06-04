---
title: Especificadores de invalidación (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: 410fe9ecc48b92c68132f7b1b8057c2549c8afcf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181907"
---
# <a name="override-specifiers--ccli-and-ccx"></a>Especificadores de invalidación (C++/CLI y C++/CX)

Los *especificadores de invalidación* modifican la forma en que se comportan los tipos heredados y los miembros de tipos heredados en los tipos derivados.

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de los especificadores de invalidación, vea:

- [abstract](abstract-cpp-component-extensions.md)

- [new (nueva ranura en vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- [Especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstract** y **sealed** también son válidos en declaraciones de tipos, donde no actúan como especificadores de invalidación.

Para información sobre cómo reemplazar explícitamente funciones de clase base, consulte [Invalidaciones explícitas](explicit-overrides-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

(No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
