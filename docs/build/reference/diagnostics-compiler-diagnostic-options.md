---
title: -diagnostics (opciones del compilador de diagnóstico) | Microsoft Docs
ms.custom: ''
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f1dce7c7c48e7c7c94da95ca187e0388b3f5d4d
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131646"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/Diagnostics (opciones del compilador de diagnóstico)  
  
Use la **/diagnostics** opción del compilador para especificar la visualización de información de ubicación del error y advertencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/diagnostics:{caret|classic|column}
```  

## <a name="remarks"></a>Comentarios  

Esta opción se admite en Visual Studio 2017 y versiones posteriores.

El **/diagnostics** opción del compilador controla la presentación de información de advertencia y error.  
  
El **/diagnostics:classic** es la opción predeterminada, que notifica solo el número de línea donde se encontró el problema.  
  
El **/diagnostics:column** opción también incluye la columna que se ha detectado el problema. Esto puede ayudarle a identificar la construcción de lenguaje específico o el carácter que está causando el problema.  
  
El **/diagnostics:caret** opción incluye la columna donde el problema se ha encontrado y coloca un símbolo de intercalación (^) en la ubicación en la línea de código donde se detectó el problema.  
  
Tenga en cuenta que en algunos casos, el compilador no detecta un problema donde se produjo. Por ejemplo, un punto y coma faltante podrían no detectarse hasta que se han detectado los símbolos de otros, inesperados. La columna se notifica y se coloca el símbolo de intercalación donde el compilador detectó que algo iba mal, que no siempre es donde tiene que realizar la corrección.  
  
El **/diagnostics** opción está disponible a partir de Visual Studio 2017.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.   
  
2. En **propiedades de configuración**, expanda el **C o C++** carpeta y elija el **General** página de propiedades.  
  
3. Use el control de lista desplegable en el **diagnósticos formato** opción de presentación del campo para seleccionar un diagnóstico. Elija **Aceptar** o **aplicar** para guardar los cambios.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)