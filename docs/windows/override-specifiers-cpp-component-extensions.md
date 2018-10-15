---
title: Especificadores de invalidación (C++ / c++ / CLI y c++ / CX) | Documentos de Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0620bc7045dcb312667cfdfe670e1f19b0545cf2
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327469"
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