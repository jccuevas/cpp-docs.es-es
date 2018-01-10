---
title: '-Zc: wchar_t (wchar_t es tipo nativo) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs: C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3375e39120fdc8f2b0d8d5502aa6def997511ff5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t es un tipo nativo)
Analice `wchar_t` como un tipo integrado conforme al estándar de C++. De forma predeterminada, **/Zc: wchar_t** se encuentra en.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Zc:wchar_t[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 Si **/Zc: wchar_t** está activado, `wchar_t` se asigna al tipo nativo específicos de Microsoft `__wchar_t`. Si **/Zc:wchar_t-** (con un signo menos) se especifica, `wchar_t` se asigna a un `typedef` para `unsigned short`. (En Visual C++ 6.0 y versiones anteriores, `wchar_t` no se implementaba como un tipo integrado, pero se declaraba en wchar.h como una declaración `typedef` de `unsigned short`). No se recomienda **/Zc:wchar_t-** porque el estándar de C++ requiere que `wchar_t` sea un tipo integrado. Si usa la versión de `typedef`, pueden producirse problemas de portabilidad. Si actualiza desde versiones anteriores de Visual C++ y encuentra un error del compilador [el error C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) porque el código intenta convertir implícitamente un `wchar_t` a `unsigned short`, le recomendamos que cambie el código para corregir el error, en su lugar de configuración **/Zc:wchar_t-**.  
  
 Microsoft implementa `wchar_t` como un valor sin signo de dos bytes. Para obtener más información acerca de `wchar_t`, consulte [intervalos de tipos de datos](../../cpp/data-type-ranges.md) y [tipos fundamentales](../../cpp/fundamental-types-cpp.md).  
  
 Si escribe código nuevo que tiene que interoperar con código más antiguo que sigue utilizando la `typedef` versión de `wchar_t`, puede proporcionar sobrecargas para ambos el `unsigned short` y `__wchar_t` variaciones de `wchar_t`, de modo que su código pueda vincularse con el código se compila con **/Zc: wchar_t** o código compilado sin él. De lo contrario, tendría que proporcionar dos compilaciones distintas de la biblioteca: una con y otra sin **/Zc: wchar_t** habilitado. Incluso en este caso, se recomienda compilar el código antiguo mediante el mismo compilador que se utiliza para compilar el código nuevo. Nunca mezcle archivos binarios compilados con compiladores diferentes.  
  
 Cuando **/Zc: wchar_t** se especifica, **_WCHAR_T_DEFINED** y **_NATIVE_WCHAR_T_DEFINED** símbolos están definidos. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md).  
  
 Si el código usa las funciones globales COM del compilador, porque **/Zc: wchar_t** es ahora de forma predeterminada, se recomienda que cambie las referencias explícitas a comsupp.lib—from el [comentario pragma](../../preprocessor/comment-c-cpp.md) o en el comando línea: a omsuppw.lib o comsuppwd.lib. (Si debe compilar con **/Zc:wchar_t-**, utilice comsupp.lib.) Si incluye el archivo de encabezado comdef.h, se especificará automáticamente la biblioteca correcta. Para obtener información sobre la compatibilidad con COM del compilador, vea [compilador COM compatible con](../../cpp/compiler-com-support.md).  
  
 El tipo `wchar_t` no se admite cuando se compila código de C. Para obtener más información acerca de los problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel izquierdo, expanda **propiedades de configuración**, **C/C++**y, a continuación, seleccione **lenguaje**.  
  
3.  Modificar el **tratar wchar_t como tipo integrado** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.  
  
## <a name="see-also"></a>Vea también  
 [/Zc (ajuste)](../../build/reference/zc-conformance.md)