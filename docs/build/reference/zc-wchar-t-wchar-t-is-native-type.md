---
title: '/ Zc: wchar_t (wchar_t es tipo nativo) | Documentos de Microsoft'
ms.custom: ''
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 061aa4a70412a0b51450470e690bea5633b764ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t es un tipo nativo)

Analice `wchar_t` como un tipo integrado conforme al estándar de C++.

## <a name="syntax"></a>Sintaxis

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>Comentarios

Si **/Zc: wchar_t** está activado, `wchar_t` es una palabra clave para un tipo entero integrado en el código compilado como C++. Si **/Zc:wchar_t-** (con un signo menos) está especificado, o en el código compilado como C, `wchar_t` no es un tipo integrado. En su lugar, `wchar_t` se define como un `typedef` para `unsigned short` en el encabezado canónica stddef.h. (La implementación de Microsoft lo define en otro encabezado que se incluye de stddef.h y otros encabezados estándares.)

No se recomienda **/Zc:wchar_t-** porque el estándar de C++ requiere que `wchar_t` sea un tipo integrado. Si usa la versión de `typedef`, pueden producirse problemas de portabilidad. Si actualiza desde versiones anteriores de Visual C++ y encuentra un error del compilador [el error C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) porque el código intenta convertir implícitamente un `wchar_t` a `unsigned short`, le recomendamos que cambie el código para corregir el error, en su lugar de configuración **/Zc:wchar_t-**.

El **/Zc: wchar_t** opción está activada de forma predeterminada en las compilaciones de C++ y se omite en compilaciones de C. El [/ permisivo-](permissive-standards-conformance.md) no afecta la opción **/Zc: wchar_t**.

Microsoft implementa `wchar_t` como un valor sin signo de dos bytes. Se asigna al tipo nativo específicos de Microsoft `__wchar_t`. Para obtener más información acerca de `wchar_t`, consulte [intervalos de tipos de datos](../../cpp/data-type-ranges.md) y [tipos fundamentales](../../cpp/fundamental-types-cpp.md).

Si escribe código nuevo que tiene que interoperar con código más antiguo que sigue utilizando la `typedef` versión de `wchar_t`, puede proporcionar sobrecargas para ambos el `unsigned short` y `__wchar_t` variaciones de `wchar_t`, de modo que su código pueda vincularse con el código se compila con **/Zc: wchar_t** o código compilado sin él. De lo contrario, tendría que proporcionar dos compilaciones distintas de la biblioteca, una con y otra sin **/Zc: wchar_t** habilitado. Incluso en este caso, se recomienda compilar el código antiguo mediante el mismo compilador que se utiliza para compilar el código nuevo. Nunca mezcle archivos binarios compilados con compiladores diferentes.

Cuando **/Zc: wchar_t** se especifica,  **\_WCHAR\_T\_DEFINED** y  **\_nativo\_WCHAR\_T\_DEFINED** símbolos están definidos. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md).

Si el código usa las funciones globales COM del compilador, porque **/Zc: wchar_t** es ahora de forma predeterminada, se recomienda que cambie las referencias explícitas a comsupp.lib (ya sea desde la [comentario pragma](../../preprocessor/comment-c-cpp.md) o en el línea de comandos) a omsuppw.lib o comsuppwd.lib. (Si debe compilar con **/Zc:wchar_t-**, utilice comsupp.lib.) Si incluye el archivo de encabezado comdef.h, se especificará automáticamente la biblioteca correcta. Para obtener información sobre la compatibilidad con COM del compilador, vea [compilador COM compatible con](../../cpp/compiler-com-support.md).

El `wchar_t` tipo integrado no se admite cuando se compila código C. Para obtener más información acerca de los problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **lenguaje** página.

1. Modificar el **tratar wchar_t como tipo integrado** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
