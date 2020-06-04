---
title: /Zc (Ajuste)
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 4422524deab2a749c96d5e967bc3223d0c9c9873
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438670"
---
# <a name="zc-conformance"></a>/Zc (Ajuste)

Puede usar las opciones del compilador **/ZC** para especificar el comportamiento del compilador estándar o específico de Microsoft.

## <a name="syntax"></a>Sintaxis

> **/Zc:** _opción_{,_opción_}

## <a name="remarks"></a>Observaciones

Cuando Visual Studio ha implementado una extensión a C C++ o que no es compatible con el estándar, puede utilizar una opción de conformidad `/Zc` para especificar el comportamiento de conformidad con el estándar o el de Microsoft. Para algunas opciones, el comportamiento específico de Microsoft es el valor predeterminado, para evitar cambios importantes a gran escala en el código existente. En otros casos, el valor predeterminado es el comportamiento estándar, en el que las mejoras en la seguridad, el rendimiento o la compatibilidad superan los costos de cambios importantes. La configuración predeterminada de cada opción de cumplimiento puede cambiar en las versiones más recientes de Visual Studio. Para obtener más información sobre cada opción de cumplimiento, vea el tema correspondiente a la opción específica. La opción del compilador [/permissive-](permissive-standards-conformance.md) establece implícitamente las opciones de conformidad que no se establecen de forma predeterminada en su configuración compatible.

Estas son las opciones del compilador de `/Zc`:

|Opción|Comportamiento|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Habilite la asignación dinámica en exceso de C++ 17 (activada de forma predeterminada en C++ 17).|
|[-de\[automático \]](zc-auto-deduce-variable-type.md)|Aplique el nuevo significado C++ estándar para `auto` (activado de forma predeterminada).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Habilite la macro **__cplusplus** para informar del estándar admitido (desactivado de forma predeterminada).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Habilitar vinculación externa para variables de `constexpr` (desactivado de forma predeterminada).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Aplique reglas C++ de ámbito de `for` estándar (activada de forma predeterminada).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Habilite el `noexcept` implícito en las funciones requeridas (activada de forma predeterminada).|
|[-de\[en línea \]](zc-inline-remove-unreferenced-comdat.md)|Quitar la función o los datos sin referencia si es COMDAT o tiene vinculación interna solamente (desactivado de forma predeterminada).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Aplique las reglas de C++ 17 noexception (activada de forma predeterminada en C++ 17 o posterior).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Un UDT temporal no se enlazará a una referencia lvalue no const (desactivada de forma predeterminada).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Aplicar reglas C++ de conversión de tipos explícitas estándar (desactivado de forma predeterminada).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Habilite las funciones de desasignación de tamaño global de C++ 14 (activada de forma predeterminada).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Deshabilitar cadena: literal para `char*` o `wchar_t*` conversión (desactivado de forma predeterminada).|
|[-de\[ternario \]](zc-ternary.md)|Aplicar reglas de operador condicional en tipos de operando (desactivado de forma predeterminada).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Habilitar la inicialización estática local segura para subprocesos (activada de forma predeterminada).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Supongamos que `operator new` inicia en caso de error (desactivado de forma predeterminada).|
|[trígrafos\[-\]](zc-trigraphs-trigraphs-substitution.md)|Habilitar trígrafos (obsoleto, desactivado de forma predeterminada).|
|[twoPhase](zc-twophase.md)|Usar el comportamiento de análisis de plantilla no conforme (de forma predeterminada).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` es un tipo nativo, no un typedef (activado de forma predeterminada).|

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
