---
title: '/ Zc: referencebinding (aplicar reglas de enlace de referencias)'
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
ms.openlocfilehash: baf2106f015a4e8557cb8469d300709694e06d84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428332"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/ Zc: referencebinding (aplicar reglas de enlace de referencias)

Cuando el **/Zc: referencebinding** se especifica la opción, el compilador no permite una referencia de valor l no constante enlazar a un archivo temporal.

## <a name="syntax"></a>Sintaxis

> **/ Zc: referencebinding**[**-**]

## <a name="remarks"></a>Comentarios

Si **/Zc: referencebinding** se especifica, el compilador sigue la sección 8.5.3 de C ++ 11 estándar y no admite expresiones que enlazan un tipo definido por el usuario temporal a una referencia de valor l no constante. De forma predeterminada, o si **/Zc:referenceBinding-** se especifica, el compilador permite tales expresiones como una extensión de Microsoft, pero se emite una advertencia de nivel 4. Para la seguridad del código, portabilidad y la conformidad, recomendamos que use **/Zc: referencebinding**.

El **/Zc: referencebinding** opción está desactivada de forma predeterminada. El [/ permissive-](permissive-standards-conformance.md) opción del compilador implícitamente establece esta opción, pero se pueden invalidar utilizando **/Zc:referenceBinding-**.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra la extensión de Microsoft que permite a un archivo temporal de un tipo definido por el usuario que se enlaza a una referencia de valor l no constante.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

void main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc: referencebinding** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
