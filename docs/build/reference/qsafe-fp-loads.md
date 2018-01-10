---
title: -Qsafe_fp_loads | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 2b2ce52d-ba57-4bd3-a739-47a7f8bfaba9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9e572c8a4d353aaee4e82e8c7bdc3f719475c03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads
Requiere instrucciones de movimiento de enteros para los valores de punto flotante y deshabilita ciertas optimizaciones de carga de punto flotante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Qsafe_fp_loads  
```  
  
## <a name="remarks"></a>Comentarios  
 **/ Qsafe_fp_loads** solo está disponible en los compiladores que tienen como destino x86; no está disponible en los compiladores destinados a x64 o ARM.  
  
 **/ Qsafe_fp_loads** fuerza al compilador que utilice instrucciones de movimiento de enteros en lugar de instrucciones de movimiento de punto flotante para mover datos entre la memoria y MMX registros. Esta opción también deshabilita la optimización de la carga del Registro para los valores de punto flotante que se pueden cargar en varias rutas cuando el valor puede producir una excepción en la carga, por ejemplo, un valor NaN.  
  
 Esta opción se reemplaza por [/fp: excepto](../../build/reference/fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** especifica un subconjunto del comportamiento del compilador especificado por **/fp: excepto**.  
  
 **/ Qsafe_fp_loads** no es compatible con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) y [/fp: Fast](../../build/reference/fp-specify-floating-point-behavior.md). Para obtener más información acerca de las opciones de compilador de punto flotante, consulte [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /Q (operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)