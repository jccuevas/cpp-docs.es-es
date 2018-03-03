---
title: -GF (eliminar cadenas duplicadas) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
dev_langs:
- C++
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d69e892fb9487b66da4dfa2a801bab302e962af7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Eliminar cadenas duplicadas)
Permite al compilador que cree una copia única de cadenas idénticas en la imagen del programa y en la memoria durante la ejecución. Se trata de una optimización denominada *la agrupación de cadenas* que pueden crear programas más pequeños.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/GF  
```  
  
## <a name="remarks"></a>Comentarios  
 Si usa **/GF**, el sistema operativo no intercambia la parte de la cadena de la memoria y puede leer el cadenas que se devuelven desde el archivo de imagen.  
  
 **/GF** agrupa las cadenas como de solo lectura. Si intenta modificar las cadenas bajo **/GF**, se produce un error de aplicación.  
  
 La agrupación de cadenas permite lo que estaban previstas como punteros de varios a varios búferes varios punteros a un único búfer. En el código siguiente, `s` y `t` se inicializan con la misma cadena. La agrupación de cadenas hace que señalen a la misma memoria:  
  
```  
char *s = "This is a character buffer";  
char *t = "This is a character buffer";  
```  
  
> [!NOTE]
>  El [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción, se utiliza para editar y continuar, establece automáticamente el **/GF** opción.  
  
> [!NOTE]
>  El **/GF** opción del compilador crea una sección direccionable para cada cadena única. Y, de forma predeterminada, un archivo objeto puede contener hasta 65.536 secciones direccionables. Si el programa contiene más de 65.536 cadenas, utilice la [/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md) opción del compilador para crear más secciones.  
  
 **/GF** está habilitada cuando [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o **/O2** se utiliza.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **generación de código** página de propiedades.  
  
4.  Modificar el **habilitar la agrupación de cadenas** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)