---
title: /Zc:referenceBinding (Aplicar reglas enlace de referencias)
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: b7e297d6fd913ddda4d44a42298a361e314af0b5
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518483"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (Aplicar reglas enlace de referencias)

Cuando se especifica la opción **/Zc: referenceBinding** , el compilador no permite que una referencia lvalue no const se enlace a un temporal.

## <a name="syntax"></a>Sintaxis

> **/Zc:referenceBinding**[ **-** ]

## <a name="remarks"></a>Notas

Si se especifica **/Zc: referenceBinding** , el compilador sigue la sección 8.5.3 del estándar c++ 11: no permite que las expresiones que enlazan un tipo definido por el usuario sean temporales a una referencia lvalue no const. De forma predeterminada, o si se especifica **/Zc: referenceBinding-** , el compilador permite tales expresiones como una extensión de Microsoft, pero se emite una advertencia de nivel 4. Para la seguridad del código, la portabilidad y la conformidad, se recomienda usar **/Zc: referenceBinding**.

La opción **/Zc: referenceBinding** está desactivada de forma predeterminada. La opción del compilador [/permissive-](permissive-standards-conformance.md) establece implícitamente esta opción, pero se puede invalidar mediante **/Zc: referenceBinding-** .

## <a name="example"></a>Ejemplo

En este ejemplo se muestra la extensión de Microsoft que permite enlazar un tipo temporal de un tipo definido por el usuario a una referencia lvalue no const.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

int main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C /C++**  > **Línea de comandos**.

1. Modifique la propiedad **opciones adicionales** para incluir **/Zc: referenceBinding** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Ajuste)](zc-conformance.md)<br/>
