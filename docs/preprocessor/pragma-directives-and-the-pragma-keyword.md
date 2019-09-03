---
title: Directivas pragma y la palabra clave __pragma
ms.date: 08/29/2019
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: 2cf075e4ff8049593a1e77c5d2c1c259b224877b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222298"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Directivas pragma y la palabra clave __pragma

Las directivas pragma especifican características del compilador específicas del equipo o del sistema operativo. La palabra clave **__pragma** , que es específica del compilador de Microsoft, le permite codificar directivas pragma dentro de definiciones de macro.

## <a name="syntax"></a>Sintaxis

> **#pragma** *token-cadena*\
> **__pragma (** *token-cadena* **)**

## <a name="remarks"></a>Comentarios

Cada implementación de C y C++ admite algunas características exclusivas del equipo host o del sistema operativo. Algunos programas, por ejemplo, deben ejercer un control preciso sobre la ubicación de los datos en memoria o controlar la manera en que determinadas funciones reciben parámetros. Las directivas de **#pragma** proporcionan un método para que cada compilador ofrezca características específicas del equipo y del sistema operativo, a la vez que mantiene C++ la compatibilidad total con los lenguajes C y.

Las pragmas son específicas del equipo o del sistema operativo por definición, y normalmente son diferentes para cada compilador. Las pragmas se pueden usar en las directivas condicionales, para proporcionar una nueva funcionalidad de preprocesador o para proporcionar información definida por la implementación al compilador.

*Token-String* es una serie de caracteres que proporciona una instrucción de compilador y argumentos concretos, si los hay. El signo de número **#** () debe ser el primer carácter que no sea un espacio en blanco en la línea que contiene la pragma. Los caracteres de espacio en blanco pueden separar el signo de número y la palabra "pragma". A continuación **#pragma**, escriba cualquier texto que el traductor pueda analizar como tokens de preprocesamiento. El argumento para **#pragma** está sujeto a la expansión de macros.

El compilador emite una advertencia cuando encuentra una pragma que no reconoce y continúa la compilación.

Los compiladores de Microsoft C y C++ reconocen las pragmas siguientes:

||||
|-|-|-|
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|
|[component](../preprocessor/component.md)|[ajustar](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|
|[intrinsic](../preprocessor/intrinsic.md)|[bucle](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|
|[managed](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)|[omp](../preprocessor/omp.md)|
|[once](../preprocessor/once.md)|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|
|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|
|[region, endregion](../preprocessor/region-endregion.md)|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|
|[setlocale](../preprocessor/setlocale.md)|[strict_gs_check](../preprocessor/strict-gs-check.md)|[unmanaged](../preprocessor/managed-unmanaged.md)|
|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|[warning](../preprocessor/warning.md)||

<sup>1</sup> solo es compatible con C++ el compilador.

## <a name="pragmas-and-compiler-options"></a>Pragmas y opciones del compilador

Algunas pragmas proporcionan la misma funcionalidad que las opciones del compilador. Cuando una pragma se encuentra en el código fuente, invalida el comportamiento especificado por la opción del compilador. Por ejemplo, si especificó [/Zp8](../build/reference/zp-struct-member-alignment.md), puede invalidar esta configuración del compilador para secciones específicas del código con [Pack](../preprocessor/pack.md):

```cmd
cl /Zp8 some_file.cpp
```

```cpp
// some_file.cpp - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8 again
// ...
```

## <a name="the-__pragma-keyword"></a>La palabra clave __pragma ()

**Específico de Microsoft**

El compilador también admite la palabra clave **__pragma** , que tiene la misma funcionalidad que la directiva **#pragma** . La diferencia es que la palabra clave **__pragma** se puede usar alineada en una definición de macro. La directiva **#pragma** no se puede usar en una definición de macro, porque el compilador interpreta el carácter de signo de número (' # ') en la Directiva como el [operador de cadena (#)](../preprocessor/stringizing-operator-hash.md).

En el ejemplo de código siguiente se muestra cómo se puede usar la palabra clave **__pragma** en una macro. Este código se ha extraído del encabezado mfcdual.h del ejemplo ACDUAL en "Ejemplos de compatibilidad COM del compilador":

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

**Finalizar específico de Microsoft**

## <a name="see-also"></a>Vea también

[Referencia deC++ C/preprocesador](../preprocessor/c-cpp-preprocessor-reference.md)\
[Pragmas de C](../c-language/c-pragmas.md)\
[Palabras clave](../cpp/keywords-cpp.md)
