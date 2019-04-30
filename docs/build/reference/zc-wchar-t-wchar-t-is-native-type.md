---
title: /Zc:wchar_t (wchar_t es un tipo nativo)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: b2563ba0ae2a07bc9f9d81128745ed4b9651fb6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315643"
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t es un tipo nativo)

Analice `wchar_t` como un tipo integrado conforme al estándar de C++.

## <a name="syntax"></a>Sintaxis

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>Comentarios

Si **/Zc:** está activado, `wchar_t` es una palabra clave para un tipo entero integrado en el código compilado como C++. Si **/Zc:wchar_t-** (con un signo menos) está especificado, o en el código compilado como C, `wchar_t` no es un tipo integrado. En su lugar, `wchar_t` se define como un `typedef` para `unsigned short` en el encabezado canónico de stddef.h. (La implementación de Microsoft lo define en otro encabezado que se incluye de forma stddef.h y otros encabezados estándares.)

No se recomienda **/Zc:wchar_t-** porque el C++ estándar requiere que `wchar_t` sea un tipo integrado. Si usa la versión de `typedef`, pueden producirse problemas de portabilidad. Si actualiza desde versiones anteriores de Visual C++ y encuentra un error del compilador [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) porque el código intenta convertir implícitamente un `wchar_t` a `unsigned short`, le recomendamos que cambie el código para corregir el error, en lugar de establecer **/Zc:wchar_t-**.

El **/Zc:** opción está activada de forma predeterminada en C++ compilaciones y se omite en compilaciones de C. El [/ permissive-](permissive-standards-conformance.md) no afecta la opción **/Zc:**.

Microsoft implementa `wchar_t` como un valor sin signo de dos bytes. Se asigna al tipo nativo específicas de Microsoft `__wchar_t`. Para obtener más información acerca de `wchar_t`, consulte [intervalos de tipos de datos](../../cpp/data-type-ranges.md) y [tipos fundamentales](../../cpp/fundamental-types-cpp.md).

Si escribe código nuevo que tiene que interoperar con código antiguo que todavía se usa el `typedef` versión de `wchar_t`, puede proporcionar sobrecargas para ambos el `unsigned short` y `__wchar_t` variaciones de `wchar_t`, de modo que su código pueda vincularse con el código se compila con **/Zc:** o código compilado sin él. De lo contrario, tendría que proporcionar dos compilaciones distintas de la biblioteca, uno con y sin **/Zc:** habilitado. Incluso en este caso, se recomienda compilar el código antiguo mediante el mismo compilador que se utiliza para compilar el código nuevo. Nunca mezcle archivos binarios compilados con compiladores diferentes.

Cuando **/Zc:** se especifica,  **\_WCHAR\_T\_DEFINED** y  **\_nativo\_WCHAR\_T\_DEFINED** símbolos están definidos. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md).

Si el código usa las funciones globales COM del compilador, porque **/Zc:** está ahora en forma predeterminada, se recomienda que cambie las referencias explícitas a comsupp.lib (ya sea desde el [pragma de comentario](../../preprocessor/comment-c-cpp.md) o en el línea de comandos) a omsuppw.lib o comsuppwd.lib. (Si se debe compilar con **/Zc:wchar_t-**, utilice comsupp.lib.) Si incluye el archivo de encabezado comdef.h, se especificará automáticamente la biblioteca correcta. Para obtener información sobre la compatibilidad con COM del compilador, vea [COM del compilador admite](../../cpp/compiler-com-support.md).

El `wchar_t` tipo integrado no se admite cuando se compila código C. Para obtener más información acerca de problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **lenguaje** página.

1. Modificar el **tratar wchar_t como tipo integrado** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)<br/>
