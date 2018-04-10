---
title: -Qfast_transcendentals (Force funciones transcendentales rápidas) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /Qfast_transcendentals
dev_langs:
- C++
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8d7e8de17c096d061653b469207352be4b9b8bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Force Fast Transcendentals)
Genera el código en línea para las funciones transcendentales.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Qfast_transcendentals  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción del compilador fuerza las funciones transcendentales a convertirse en código insertado para mejorar la velocidad de ejecución. Esta opción tiene un efecto solo cuando se emparejan con **/fp: excepto** o **/fp: precisa**. Generar código en línea para las funciones transcendentales ya es el comportamiento predeterminado en **/fp: Fast**.  
  
 Esta opción no es compatible con **/fp: strict**. Vea [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md) para obtener más información acerca de opciones del compilador de punto de flotante.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /Q (operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)