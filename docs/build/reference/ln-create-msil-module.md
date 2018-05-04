---
title: -LN (crear un módulo MSIL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /LN
dev_langs:
- C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 918b3857c2e6f26a7f2e11614a00049e9b615ea8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ln-create-msil-module"></a>/LN (Crear un módulo MSIL)
Especifica que no se debe insertar un manifiesto de ensamblado en el archivo de salida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/LN  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, **/LN** no está en vigor (un manifiesto del ensamblado se inserta en el archivo de salida).  
  
 Cuando **/LN** se utiliza, uno de los [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) opciones también se deben usar.  
  
 Un programa administrado que no tiene metadatos de ensamblado en el manifiesto se denomina módulo. Si se compila con [/c (compilar sin vincular)](../../build/reference/c-compile-without-linking.md) y **/LN**, especifique [/NOASSEMBLY (crear un módulo MSIL)](../../build/reference/noassembly-create-a-msil-module.md) en la fase del vinculador para crear el archivo de salida.  
  
 Puede que desee crear módulos si desea seguir un enfoque basado en componentes para generar ensamblados.  Es decir, puede crear los tipos y compilarlos en módulos.  A continuación, puede generar un ensamblado de uno o varios módulos.  Para obtener más información sobre cómo crear ensamblados de módulos, vea [archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md) o [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).  
  
 La extensión de archivo predeterminada para un módulo es. netmodule.  
  
 En [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] versiones anteriores a Visual C++ 2005, un módulo creado con **/CLR: noAssembly**.  
  
 El vinculador de Visual C++ acepta archivos .netmodule como entrada y el archivo de salida generado por el vinculador será un ensamblado o archivo .netmodule sin ninguna dependencia de tiempo de ejecución en cualquiera de los archivos .netmodule que se utilizaron como entrada al vinculador.  Para más información, consulte [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
-   Especifique [/NOASSEMBLY (crear un módulo MSIL)](../../build/reference/noassembly-create-a-msil-module.md) en la fase del vinculador para crear el archivo de salida.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Esta opción del compilador no se puede cambiar mediante programación.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)