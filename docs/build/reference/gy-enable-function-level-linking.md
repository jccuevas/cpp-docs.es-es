---
title: -Gy (habilitar vinculación en el nivel de función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
dev_langs:
- C++
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36e939a12cf23a9d9e476b676a5b068889414497
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376304"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Habilitar vinculación en el nivel de función)
Permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas (COMDATs).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Gy[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 El vinculador requiere que las funciones se empaquetan por separado como COMDAT para excluir u ordenar funciones individuales en un archivo DLL o .exe.  
  
 Puede usar la opción del vinculador [especificación /OPT (optimizaciones)](../../build/reference/opt-optimizations.md) para impedir que el archivo .exe las funciones empaquetadas.  
  
 Puede usar la opción del vinculador [/ORDER (colocar funciones en orden)](../../build/reference/order-put-functions-in-order.md) para incluir las funciones empaquetadas en un orden especificado en el archivo .exe.  
  
 Las funciones inline siempre se empaquetan si sus instancias se crean como llamadas (lo que ocurre, por ejemplo, si los procesos inline están desactivados o si se toma una dirección de función). Además, las funciones de miembro de C++ definidas en la declaración de clase se empaquetan de manera automática; otras funciones no son y, al seleccionar esta opción es necesaria para compilarlos como funciones empaquetadas.  
  
> [!NOTE]
>  El [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción, se utiliza para editar y continuar, establece automáticamente el **/Gy** opción.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **generación de código** página de propiedades.  
  
4.  Modificar el **habilitar vinculación en el nivel de función** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)