---
title: "/Zc:wchar_t (wchar_t es un tipo nativo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType"
  - "VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType"
  - "/Zc:wchar_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc (opción del compilador) [C++]"
  - "ajuste (opción del compilador)"
  - "wchar_t (tipo)"
  - "Zc (opción del compilador) [C++]"
  - "-Zc (opción del compilador) [C++]"
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /Zc:wchar_t (wchar_t es un tipo nativo)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Analice `wchar_t` como un tipo integrado conforme al estándar de C\+\+.  La opción **\/Zc:wchar\_t** está activada de manera predeterminada.  
  
## Sintaxis  
  
```  
/Zc:wchar_t[-]  
```  
  
## Comentarios  
 Si **\/Zc:wchar\_t** está activado, `wchar_t` se asigna al tipo nativo especifico de Microsoft `__wchar_t`.  Si se especifica **\/Zc:wchar\_t\-** \(con un signo menos\), `wchar_t` se asigna a una definición `typedef` de `unsigned short`.  \(En Visual C\+\+ 6.0 y versiones anteriores, `wchar_t` no se implementaba como un tipo integrado, pero se declaraba en wchar.h como una declaración `typedef` de `unsigned short`\). No se recomienda usar **\/Zc:wchar\_t\-**, ya que el estándar de C\+\+ requiere que `wchar_t` sea un tipo integrado.  Si usa la versión de `typedef`, pueden producirse problemas de portabilidad.  Si actualiza desde versiones anteriores de Visual C\+\+ y encuentra un error del compilador [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) porque el código intenta convertir implícitamente un tipo `wchar_t` en `unsigned short`, es recomendable cambiar el código para corregir el error en lugar de establecer **\/Zc:wchar\_t\-**.  
  
 Microsoft implementa `wchar_t` como un valor sin signo de dos bytes.  Para obtener más información acerca de `wchar_t`, vea [Intervalos de tipos de datos](../../cpp/data-type-ranges.md) y [Tipos fundamentales](../../cpp/fundamental-types-cpp.md).  
  
 Si escribe código nuevo que tiene que interoperar con un código anterior que sigue utilizando la versión `typedef` de `wchar_t`, puede proporcionar sobrecargas para las dos variantes `unsigned short` y `__wchar_t` de `wchar_t`, de modo que el código pueda vincularse con el código compilado mediante **\/Zc:wchar\_t** o el código compilado sin él.  De lo contrario, tendría que proporcionar dos compilaciones distintas de la biblioteca: una con **\/Zc:wchar\_t** habilitado y otra sin él.  Incluso en este caso, se recomienda compilar el código antiguo mediante el mismo compilador que se utiliza para compilar el código nuevo.  Nunca mezcle archivos binarios compilados con compiladores diferentes.  
  
 Cuando se especifica **\/Zc:wchar\_t**, se definen los símbolos **\_WCHAR\_T\_DEFINED** y **\_NATIVE\_WCHAR\_T\_DEFINED**.  Para obtener más información, vea [Macros predefinidas](../../preprocessor/predefined-macros.md).  
  
 Si el código usa las funciones globales COM del compilador, dado que **\/Zc:wchar\_t** ahora está habilitado de forma predeterminada, se recomienda cambiar las referencias explícitas a comsupp.lib \(de [pragma comment](../../preprocessor/comment-c-cpp.md) o línea de comandos a omsuppw.lib o comsuppwd.lib\).  \(Si debe compilar con **\/Zc:wchar\_t\-**, utilice comsupp.lib\). Si incluye el archivo de encabezado comdef.h, se especificará automáticamente la biblioteca correcta.  Para obtener información sobre la compatibilidad con COM del compilador, vea [Compatibilidad con COM del compilador](../../cpp/compiler-com-support.md).  
  
 El tipo `wchar_t` no se admite cuando se compila código de C.  Para obtener más información sobre los problemas de conformidad con Visual C\+\+, vea [Comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel de la izquierda, expanda **Propiedades de configuración**, **C\/C\+\+** y, a continuación, seleccione **Lenguaje**.  
  
3.  Modifique la propiedad **Tratar wchar\_t como tipo integrado**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.  
  
## Vea también  
 [\/Zc \(Ajuste\)](../../build/reference/zc-conformance.md)