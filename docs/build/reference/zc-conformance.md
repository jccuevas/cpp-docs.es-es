---
title: /Zc (ajuste) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zc
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fd2ec208e872e05f8329bf5e077a74403d0c612
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716058"
---
# <a name="zc-conformance"></a>/Zc (Ajuste)

Puede usar el **/Zc** opciones del compilador para especificar el comportamiento del compilador estándar o específico de Microsoft.

## <a name="syntax"></a>Sintaxis

> **/ Zc:**_opción_{,_opción_}

## <a name="remarks"></a>Comentarios

Cuando Visual Studio ha implementado una extensión de C o C++ que no es compatible con el estándar, puede usar un `/Zc` opción conformidad para especificar el comportamiento que cumplen el estándar o específico de Microsoft. Para algunas opciones, el comportamiento específico de Microsoft es el predeterminado, para evitar cambios importantes a gran escala en el código existente. En otros casos, el valor predeterminado es el comportamiento estándar, donde las mejoras en seguridad, rendimiento o compatibilidad superan los costes de los principales cambios. Puede cambiar la configuración predeterminada de cada opción de conformidad en versiones más recientes de Visual Studio. Para obtener más información acerca de cada opción de conformidad, vea el tema para la opción específica. El [/ permissive-](permissive-standards-conformance.md) opción del compilador implícitamente establece las opciones de conformidad que no se establecen de forma predeterminada para su configuración de la función.

Estos son los `/Zc` opciones del compilador:

|Opción|Comportamiento|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Habilitar C ++ 17 asignación alineada en exceso dinámico (activado de forma predeterminada en C ++ 17).|
|[Automático\[-\]](zc-auto-deduce-variable-type.md)|Aplicar el nuevo significado estándar de C++ para `auto` (de forma predeterminada).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Habilitar la **__cplusplus** macro para notificar el estándar admitido (desactivado de forma predeterminada).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Habilitar vinculación externa para `constexpr` variables (desactivado de forma predeterminada).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Exigir Standard C++ `for` las reglas de ámbito (de forma predeterminada).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Habilitar implícita `noexcept` en funciones requeridas (en forma predeterminada).|
|[en línea\[-\]](zc-inline-remove-unreferenced-comdat.md)|Quitar datos o función sin referencia si son COMDAT o solo tienen vinculación interna (desactivado de forma predeterminada).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Exigir reglas C ++ 17 noexcept (de forma predeterminada en C ++ 17 o posterior).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Un archivo temporal UDT no se enlazará a una referencia distinta de const lvalue (desactivado de forma predeterminada).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Exigir reglas de conversión explícita de tipos estándar de C++ (desactivado de forma predeterminada).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Permitir a C ++ 14 desasignación con tamaño global funciones (de forma predeterminada).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Deshabilitar literal de cadena `char*` o `wchar_t*` conversión (desactivado de forma predeterminada).|
|[Ternario\[-\]](zc-ternary.md)|Aplicar reglas de operador condicional en los tipos de operandos (desactivado de forma predeterminada).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Habilitar la inicialización estática local de subprocesos (de forma predeterminada).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Suponga `operator new` en caso de error (desactivado de forma predeterminada).|
|[Trígrafos\[-\]](zc-trigraphs-trigraphs-substitution.md)|Habilitar trígrafos (obsoletos, desactivado de forma predeterminada).|
|[twoPhase-](zc-twophase.md)|Usar análisis de comportamiento (cumple las especificaciones de forma predeterminada) de las plantillas no conforme.|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` es un tipo nativo, no un typedef (de forma predeterminada).|

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Vea también

[Opciones del compilador](compiler-options.md)<br/>
[Establecer las opciones del compilador](setting-compiler-options.md)
