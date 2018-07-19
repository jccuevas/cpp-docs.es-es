---
title: -STACK (asignaciones de la pila) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
dev_langs:
- C++
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8ee3fac90bcbb972278d9b3e2cf7cebd62fedf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377881"
---
# <a name="stack-stack-allocations"></a>/STACK (Asignaciones de la pila)
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /STACK establece el tamaño en bytes de la pila. Solo debe usar esta opción cuando compile un archivo .exe.  
  
 El valor `reserve` especifica la asignación total de la pila en la memoria virtual. Para los equipos ARM, x86 y [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], el tamaño de pila predeterminado es de 1 MB.  
  
 El argumento `commit` está sujeto a interpretación por el sistema operativo. En Windows/Windows RT especifica la cantidad de memoria física que se debe asignar de una sola vez. La memoria virtual confirmada hace que se reserve espacio en el archivo de paginación. Si se asigna un valor mayor a `commit`, se ahorrará tiempo cuando la aplicación necesite más espacio de la pila, pero aumentarán los requisitos de memoria y, posiblemente, el tiempo de inicio. Para los equipos ARM, x86 y [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], el valor de confirmación predeterminado es de 4 kB.  
  
 Especifique los valores `reserve` y `commit` en notación decimal o en la notación del lenguaje C.  
  
 Otra manera de establecer el tamaño de la pila es con la [STACKSIZE](../../build/reference/stacksize.md) instrucción en un archivo de definición de módulos (.def). **STACKSIZE** reemplaza las asignaciones de pila (/ de la pila) opción si se especifican ambos. Puede cambiar el tamaño de pila después de que el archivo .exe se compila mediante la [EDITBIN](../../build/reference/editbin-reference.md) herramienta.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **System** página de propiedades.  
  
4.  Modifique una de las propiedades siguientes:  
  
    -   **Tamaño de confirmación de la pila**  
  
    -   **Tamaño de reserva de la pila**  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)