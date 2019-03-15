---
title: '/ Zc: __cplusplus (macro __cplusplus actualizada de habilitar)'
ms.date: 05/30/2018
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 89545f541f32374a47dce7f87958e61873c1b47c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810099"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/ Zc: __cplusplus (macro __cplusplus actualizada de habilitar)

El **/Zc: __cplusplus** habilita la opción del compilador la  **\_ \_cplusplus** macro de preprocesador para informar de un valor actualizado de soporte técnico recientes estándares de lenguaje C++. De forma predeterminada, Visual Studio siempre devuelve el valor "199711L" para el  **\_ \_cplusplus** macro de preprocesador.

## <a name="syntax"></a>Sintaxis

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>Comentarios

El  **\_ \_cplusplus** macro de preprocesador sirve principalmente al soporte técnico de informes para una determinada versión del estándar de C++. Dado que parece una gran cantidad de código existente que dependen del valor de esta macro coincidencia "199711L", el compilador no cambia el valor de la macro a menos que explícitamente participa en esta opción mediante el uso de la **/Zc: __cplusplus** opción del compilador. El **/Zc: __cplusplus** opción está disponible a partir de Visual Studio 2017 versión 15.7 y está desactivada de forma predeterminada. En versiones anteriores de Visual Studio y de forma predeterminada, o si **/Zc:__cplusplus-** se especifica, Visual Studio devuelve el valor "199711 L" para el  **\_ \_cplusplus** macro de preprocesador. El [/ permissive-](permissive-standards-conformance.md) no habilita la opción **/Zc: __cplusplus**.

Cuando el **/Zc: __cplusplus** opción está habilitada, el valor indicado por el  **\_ \_cplusplus** depende de la macro el [/STD](std-specify-language-standard-version.md) conmutador de versión configuración de. Esta tabla muestran los valores posibles para la macro:

|/ Zc: __cplusplus conmutador|conmutador /std:c++|valor __cplusplus|
|-|-|-|
Zc:__cplusplus|/ std: c ++ 14 (valor predeterminado)|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/ std: c ++ más reciente|201704L
Zc:__cplusplus-(deshabilitado)|Cualquier valor|199711L
No se especifica|Cualquier valor|199711L

El compilador no admite conmutadores de estándares para C ++ 11, C ++ 03 o C ++ 98.

Para la detección más precisa de los cambios realizados en el conjunto de herramientas del compilador, utilice la [_MSC_VER](../../preprocessor/predefined-macros.md) la macro predefinida. El valor de esta macro integrada se incrementa para cada actualización del conjunto de herramientas en Visual Studio 2017 y versiones posteriores. El [_MSVC_LANG](../../preprocessor/predefined-macros.md) la macro predefinida informa de si la versión estándar del **/Zc: __cplusplus** opción está habilitada o deshabilitada. Cuando **/Zc: __cplusplus** está habilitada, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Agregar **/Zc: __cplusplus** o **/Zc:__cplusplus-** a la **opciones adicionales:** panel.

## <a name="see-also"></a>Vea también

- [/Zc (Ajuste)](zc-conformance.md)
- [/STD (versión estándar del lenguaje especifique)](std-specify-language-standard-version.md)
- [Macros predefinidas](../../preprocessor/predefined-macros.md)
