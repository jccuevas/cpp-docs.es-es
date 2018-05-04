---
title: -ZW (compilación de Windows en tiempo de ejecución) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
dev_langs:
- C++
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fce6c6825ed4ae715a2f4cde6b0e1ffa8b3b6733
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (Compilación de Windows Runtime)
Compila el código fuente para admitir [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) para la creación de aplicaciones de la plataforma Universal de Windows (UWP).  
  
 Cuando usas **/ZW** para compilar, especifique siempre **/EHsc** así.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
/ZW /EHsc  
/ZW:nostdlib /EHsc  
```  
  
## <a name="arguments"></a>Argumentos  
 nostdlib  
 Indica que Platform.winmd, Windows.Foundation.winmd y otros archivos de metadatos de Windows (.winmd) predeterminados no se incluyen automáticamente en la compilación, En su lugar, debe utilizar el [/FU (Name Forced #using archivo)](../../build/reference/fu-name-forced-hash-using-file.md) opción del compilador para especificar explícitamente los archivos de metadatos de Windows.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se especifica la **/ZW** opción, el compilador admite estas características:  
  
-   Los archivos de metadatos necesarios, los espacios de nombres, tipos de datos y funciones que requiere la aplicación para ejecutarse en el tiempo de ejecución de Windows.  
  
-   Automático recuento de referencias de objetos en tiempo de ejecución de Windows y automática de descarte de un objeto cuando su recuento de referencias llega a cero.  
  
 Dado que el vinculador incremental no es compatible con los metadatos de Windows incluidos en los archivos .obj mediante la **/ZW** opción, el [/Gm (habilitar recompilación mínima)](../../build/reference/gm-enable-minimal-rebuild.md) no es compatible con la opción  **/ZW**.  
  
 Para obtener más información, consulte [referencia del lenguaje Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)