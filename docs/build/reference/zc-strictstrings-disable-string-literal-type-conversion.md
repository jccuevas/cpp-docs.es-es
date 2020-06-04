---
title: /Zc:strictStrings (Deshabilitar conversión de tipo de literal de cadena)
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: 954088955a3f1530bb298aadbc35c7dd74150b7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315669"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (Deshabilitar conversión de tipo de literal de cadena)

Cuando se especifica, el compilador requiere que los punteros inicializados con literales de cadena cumplan estrictamente las cualificaciones de `const`.

## <a name="syntax"></a>Sintaxis

> **/Zc:strictStrings**[**-**]

## <a name="remarks"></a>Comentarios

Si **/Zc: strictstrings** se especifica, el compilador exige el estándar de C++ `const` calificaciones de los literales de cadena, como el tipo ' matriz de `const char`' o ' matriz de `const wchar_t`', en función de la declaración. Los literales de cadena son inmutables, y si trata de modificar el contenido de uno, se producirá un error de infracción de acceso en tiempo de ejecución. Debe declarar un puntero de cadena como `const` para inicializarlo con un literal de cadena o usar una `const_cast` explícita para inicializar un puntero no `const`. De forma predeterminada, o si **/Zc:strictStrings-** se especifica, el compilador no exige el estándar de C++ `const` calificaciones de los punteros de cadena inicializados con literales de cadena.

El **/Zc: strictstrings** opción está desactivada de forma predeterminada. El [/ permissive-](permissive-standards-conformance.md) opción del compilador implícitamente establece esta opción, pero se pueden invalidar utilizando **/Zc:strictStrings-**.

Use la **/Zc: strictstrings** opción para evitar la compilación de código incorrecto. En este ejemplo, se muestra cómo un simple error de declaración provoca un bloqueo en tiempo de ejecución:

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

Cuando **/Zc: strictstrings** está habilitado, el mismo código informa de un error en la declaración de `str`.

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

Si usa `auto` para declarar un puntero de cadena, el compilador creará automáticamente la declaración del tipo de puntero `const` correcta. Si trata de modificar el contenido de un puntero `const`, el compilador informará de ello en forma de error.

> [!NOTE]
> La biblioteca estándar de C++ en Visual Studio 2013 no admite la **/Zc: strictstrings** se basa en la opción del compilador en modo de depuración. Si ve varios [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) de salida de errores en la compilación, esto puede ser la causa.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc: strictstrings** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)<br/>
