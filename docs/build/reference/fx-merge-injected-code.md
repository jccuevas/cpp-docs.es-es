---
title: "-Fx (combinar código insertado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
dev_langs: C++
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 344d9ded0cdb77abfc2fa53ab4180f2e484b7dc9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="fx-merge-injected-code"></a>/Fx (Combinar código insertado)
Genera una copia de cada archivo de origen con código insertado combinado en el origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Fx  
```  
  
## <a name="remarks"></a>Comentarios  
 Para distinguir un archivo de origen combinado de un archivo de origen original, **/Fx** agrega una extensión .mrg entre el nombre de archivo y la extensión de archivo. Por ejemplo, un archivo denominado MyCode.cpp que contiene código con atributos creado con **/Fx** crea un archivo denominado MyCode.mrg.cpp que contiene el código siguiente:  
  
```  
//+++ Start Injected Code  
[no_injected_text(true)];      // Suppress injected text, it has   
                               // already been injected  
#pragma warning(disable: 4543) // Suppress warnings about skipping   
                               // injected text  
#pragma warning(disable: 4199) // Suppress warnings from attribute   
                               // providers  
//--- End Injected Code  
```  
  
 En un archivo .mrg, el código insertado a causa de un atributo se delimita de la siguiente manera:  
  
```  
//+++ Start Injected Code  
...  
//--- End Injected Code  
```  
  
 El atributo [no_injected_text](../../windows/no-injected-text.md) está insertado en un archivo .mrg, lo que permite la compilación del archivo .mrg sin volver a insertar texto.  
  
 Debe tener en cuenta que el archivo de origen .mrg está diseñado para ser una representación del código fuente insertado por el compilador. Es posible que el archivo .mrg no se compile ni ejecute exactamente como el archivo de origen.  
  
 Las macros no se expanden en el archivo .mrg.  
  
 Si el programa incluye un archivo de encabezado que usa código insertado, **/Fx** genera un archivo .mrg.h para ese encabezado. **/Fx** no combina archivos incluidos que no usan código insertado.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Archivos de salida** .  
  
4.  Modifique la propiedad **Código fuente con atributos expandidos** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)