---
title: -Zc (ajuste) | Documentos de Microsoft
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /zc
dev_langs: C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86b12604a5348c3a1aabb33c7e13a4e7a3c57932
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zc-conformance"></a>/Zc (Ajuste)

Puede usar el **/Zc** opciones del compilador para especificar el comportamiento del compilador estándar o específico de Microsoft.

## <a name="syntax"></a>Sintaxis

> / Zc:_opción_{,_opción_}

## <a name="remarks"></a>Comentarios

Cuando Visual Studio haya implementado una extensión de C o C++ que no es compatible con el estándar, puede usar un `/Zc` opción de conformidad para especificar el comportamiento que cumplen el estándar o específico de Microsoft. Para algunas opciones, el comportamiento específico de Microsoft es el predeterminado, para evitar cambios importantes a gran escala en el código existente. En otros casos, el valor predeterminado es el comportamiento estándar, donde las mejoras de seguridad, rendimiento o compatibilidad compensan los costos de los principales cambios. El valor predeterminado de cada opción de cumplimiento puede cambiar en versiones más recientes de Visual Studio. Para obtener más información acerca de cada opción de conformidad, vea el tema de cada opción específica.

Estos son los `/Zc` opciones del compilador:

|Opción|Comportamiento|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Habilitar C ++ 17 exceso dinámica asignación alineadas (activado de forma predeterminada en C ++ 17).|
|[Automático\[-\]](zc-auto-deduce-variable-type.md)|Exigir el significado de C++ estándar nueva para `auto` (de forma predeterminada).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Habilitar vinculación externa para `constexpr` variables (desactivado de forma predeterminada).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Exigir Standard C++ `for` las reglas de ámbito (de forma predeterminada).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Habilitar implícita `noexcept` en las funciones necesarias (de forma predeterminada).|
|[en línea\[-\]](zc-inline-remove-unreferenced-comdat.md)|Quitar función sin referencia o los datos si se COMDAT o tiene vinculación interna solo (desactivado de forma predeterminada).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Aplicar C ++ 17 noexcept reglas (de forma predeterminada en C ++ 17 o posterior).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Un archivo temporal UDT no se enlazará a una referencia lvalue no es const (desactivado de forma predeterminada).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Aplicar reglas de conversión de tipos explícita de estándar de C++ (desactivado de forma predeterminada).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Habilitar C ++ 14 desasignación con tamaño global funciones (de forma predeterminada).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Deshabilitar el literal de cadena a `char*` o `wchar_t*` conversión (desactivado de forma predeterminada).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Habilitar la inicialización local estática de subprocesos (de forma predeterminada).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Suponga `operator new` produce en caso de error (desactivado de forma predeterminada).|
|[trígrafos\[-\]](zc-trigraphs-trigraphs-substitution.md)|Habilitar trígrafos (obsoletas, desactivado de forma predeterminada).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t`es un tipo nativo, no en una definición de tipo (de forma predeterminada).|

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Vea también

[Opciones del compilador](compiler-options.md)  
[Establecer las opciones del compilador](setting-compiler-options.md)
