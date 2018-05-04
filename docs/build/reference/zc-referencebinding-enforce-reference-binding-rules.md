---
title: /Zc:referenceBinding (exigir reglas de enlace de referencia) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30038f6ff73eaa2d9536c3685927458a70209864
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (exigir reglas de enlace de referencia)

Cuando el **/Zc:referenceBinding** se especifica la opción, el compilador no permite una referencia de valor l no es const enlazar a un archivo temporal.

## <a name="syntax"></a>Sintaxis

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>Comentarios

Si **/Zc:referenceBinding** se especifica, el compilador sigue la sección 8.5.3 del estándar C ++ 11 y no admite expresiones que enlazan un tipo definido por el usuario temporal con una referencia de valor l no constantes. De forma predeterminada, o si **/Zc:referenceBinding-** se especifica, el compilador permite estas expresiones como una extensión de Microsoft, pero se emite una advertencia de nivel 4. Seguridad de código, portabilidad y conformidad, recomendamos que use **/Zc:referenceBinding**.

El **/Zc:referenceBinding** opción está desactivada de forma predeterminada. El [/ permisivo-](permissive-standards-conformance.md) opción del compilador implícitamente establece esta opción, pero se puede invalidar usando **/Zc:referenceBinding-**.

## <a name="example"></a>Ejemplo

Este ejemplo muestra la extensión de Microsoft que permite a un archivo temporal de un tipo definido por el usuario se puede enlazar a una referencia de valor l no constantes.

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zc:referenceBinding** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
