---
title: "-Zp (alineación de miembros de estructura) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
dev_langs: C++
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d387e0ab020e96afb3e2975b5c8686b668cbc10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zp-struct-member-alignment"></a>/Zp (Alineación de miembros de estructura)
Controla cómo se empaquetan los miembros de una estructura en la memoria y especifica el mismo tipo de empaquetado para todas las estructuras de un módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Zp[1|2|4|8|16]  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando se especifica esta opción, los miembros de estructura después del primero se almacenan en el tamaño del tipo de miembro o `n`-límites de bytes (donde `n` es 1, 2, 4, 8 o 16), lo que sea menor.  
  
 Los valores disponibles se describen en la tabla siguiente.  
  
 1  
 Empaqueta las estructuras en límites de 1 byte. Igual que **/Zp**.  
  
 2  
 Empaqueta las estructuras en límites de 2 bytes.  
  
 4  
 Empaqueta las estructuras en límites de 4 bytes.  
  
 8  
 Empaqueta las estructuras en límites de 8 bytes (valor predeterminado).  
  
 16  
 Empaqueta las estructuras en límites de 16 bytes.  
  
 No se debe usar esta opción a menos que tenga requisitos de alineación específica.  
  
 También puede usar [pack](../../preprocessor/pack.md) empaquetado de estructura de control. Para obtener más información sobre la alineación, vea:  
  
-   [align](../../cpp/align-cpp.md)  
  
-   [__alignof (Operador)](../../cpp/alignof-operator.md)  
  
-   [__unaligned](../../cpp/unaligned.md)  
  
-   [Ejemplos de alineación de estructuras](../../build/examples-of-structure-alignment.md) (x64 específico)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **generación de código** página de propiedades.  
  
4.  Modificar el **alineación de miembros de Struct** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)