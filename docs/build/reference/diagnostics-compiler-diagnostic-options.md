---
title: "-diagnósticos (opciones del compilador diagnóstico) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/11/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs:
- C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a1c893b530bfa895e5ec127bd0aea2fb0df4ff3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/Diagnostics (opciones del compilador diagnóstico)  
  
Use la **/diagnostics** opción del compilador para especificar la visualización de información de ubicación de error y advertencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/diagnostics:{caret|classic|column}
```  

## <a name="remarks"></a>Comentarios  
El **/diagnostics** opción del compilador controla la presentación de información de advertencia y error.  
  
El **/diagnostics:classic** es la opción predeterminada, que indica sólo el número de línea donde se encontró el problema.  
  
El **/diagnostics:column** opción también incluye la columna donde se encontró el problema. Esto puede ayudarle a identificar la construcción de lenguaje específico o el carácter que está causando el problema.  
  
El **/diagnostics:caret** opción incluye la columna donde se encontró el problema y la coloca un símbolo de intercalación (^) en la ubicación en la línea de código donde se detectó el problema.  
  
Tenga en cuenta que en algunos casos, el compilador no detecta un problema donde se produjo. Por ejemplo, un punto y coma faltante podrían no detectarse hasta que se han encontrado símbolos de otros, inesperados. Se notifica la columna y el símbolo de intercalación se coloca en el compilador detectó que algo no es correcto, que no siempre es donde es necesario realizar la corrección.  
  
El **/diagnostics** opción está disponible a partir de Visual Studio de 2017.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.   
  
2. En **propiedades de configuración**, expanda la **C/C++** carpeta y elija el **General** página de propiedades.  
  
3. Utilice el control de lista desplegable en el **diagnósticos formato** opción de visualización de campos para seleccionar un diagnóstico. Elija **Aceptar** o **aplicar** para guardar los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)