---
title: /Zc:__cplusplus (habilitar actualizada __cplusplus (macro))
ms.custom: ''
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:__cplusplus
dev_langs:
- C++
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a796794c0086b09c15ee88442e0fea4d1b114d98
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705722"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (habilitar actualizada __cplusplus (macro))

El **/Zc:__cplusplus** compilador opción habilita la  **\_ \_cplusplus** macro de preprocesador para informar de un valor para la compatibilidad con estándares de lenguaje de reciente C++ actualizado. De forma predeterminada, Visual Studio siempre devuelve el valor "199711" L"para el  **\_ \_cplusplus** macro de preprocesador.

## <a name="syntax"></a>Sintaxis

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>Comentarios

El  **\_ \_cplusplus** macro de preprocesador se utiliza normalmente para admitir informes para una versión concreta del estándar de C++. Debido a una gran cantidad de código existente parece dependen del valor de esta macro coincidencia "199711" L", el compilador no cambia el valor de la macro a menos que explícitamente participar en mediante el uso de la **/Zc:__cplusplus** opción del compilador. El **/Zc:__cplusplus** opción está disponible a partir de Visual Studio 2017 versión 15,7 y está desactivada de forma predeterminada. En versiones anteriores de Visual Studio y de forma predeterminada, o si **/Zc:__cplusplus-** se especifica, Visual Studio devuelve el valor "199711" L"para el  **\_ \_cplusplus** macro de preprocesador. El [/ permisivo-](permissive-standards-conformance.md) no habilita la opción **/Zc:__cplusplus**.

Cuando el **/Zc:__cplusplus** opción está habilitada, el valor notificado por el  **\_ \_cplusplus** depende de la macro el [/std](std-specify-language-standard-version.md) conmutador de versión configuración de. Esta tabla muestra los valores posibles de la macro:

|Conmutador /Zc:__cplusplus|conmutador /std:c++|valor de __cplusplus|
|-|-|-|
Zc:__cplusplus|/std:c ++ 14 (valor predeterminado)|201402L
Zc:__cplusplus|/std:c ++ 17|201703L
Zc:__cplusplus|/std:c ++ más reciente|201704L
Zc:__cplusplus-(deshabilitado)|Cualquier valor|199711L
No se ha especificado|Cualquier valor|199711L

El compilador no admite conmutadores de estándares de C ++ 98, C ++ 03 o C ++ 11.

Para la detección más precisa de los cambios en el conjunto de herramientas del compilador, utilice la [_MSC_VER](../../preprocessor/predefined-macros.md) macro predefinida. El valor de esta macro integrada se incrementa para cada actualización de conjunto de herramientas en Visual Studio de 2017 y versiones posteriores. El [_MSVC_LANG](../../preprocessor/predefined-macros.md) macro predefinida informa de si la versión estándar del **/Zc:__cplusplus** opción está habilitada o deshabilitada. Cuando **/Zc:__cplusplus** está habilitada, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Agregar **/Zc:__cplusplus** o **/Zc:__cplusplus-** a la **opciones adicionales:** panel.

## <a name="see-also"></a>Vea también

- [/Zc (Ajuste)](zc-conformance.md)
- [/STD (versión estándar del lenguaje de especificar)](std-specify-language-standard-version.md)
- [Macros predefinidas](../../preprocessor/predefined-macros.md)
