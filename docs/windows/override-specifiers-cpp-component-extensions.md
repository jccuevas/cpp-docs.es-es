---
title: Especificadores de invalidación (C++ / c++ / CLI y c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: 9d839b9530cff144cda7897b0c96af48c14454a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639861"
---
# <a name="override-specifiers--ccli-and-ccx"></a>Especificadores de invalidación (C++ / c++ / CLI y c++ / CX)

*Especificadores de invalidación* modificar tipos cómo heredados y miembros de tipos heredados se comportan en tipos derivados.

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de los especificadores de invalidación, vea:

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [New (nueva ranura en vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- [Especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstracta** y **sealed** también son válidos en declaraciones de tipos, donde no actúan como especificadores de invalidación.

Para obtener información sobre cómo reemplazar explícitamente funciones de clase base, vea [invalidaciones explícitas](../windows/explicit-overrides-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

(No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)