---
title: -Zl (omitir nombres de biblioteca predeterminada) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
dev_langs:
- C++
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f09abebb8fc142bbe2390f61d790a5885c9aebe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707322"
---
# <a name="zl-omit-default-library-name"></a>/Zl (Omitir nombres de biblioteca predeterminada)

Omite el nombre de biblioteca predeterminado en tiempo de ejecución de C desde el archivo .obj. De forma predeterminada, el compilador sitúa el nombre de la biblioteca en el archivo .obj para dirigir el enlazador hacia la biblioteca correcta.

## <a name="syntax"></a>Sintaxis

```
/Zl
```

## <a name="remarks"></a>Comentarios

Para obtener más información acerca de la biblioteca predeterminada, vea [utilizar la biblioteca en tiempo de ejecución](../../build/reference/md-mt-ld-use-run-time-library.md).

Puede usar **/Zl** para compilar archivos .obj que piense incluir en una biblioteca. Aunque si se omite el nombre de la biblioteca guarda sólo una pequeña cantidad de espacio para un solo archivo .obj, el ahorro de espacio total es significativo en una biblioteca que contiene muchos módulos de objeto.

Esta opción es una opción avanzada. Al establecer esta opción quita cierta compatibilidad de biblioteca en tiempo de ejecución de C que puede ser necesario para la aplicación, lo que produce errores en tiempo de vínculo si la aplicación depende de esta compatibilidad. Si usa esta opción debe proporcionar los componentes necesarios de alguna otra manera.

Use [/NODEFAULTLIB (Omitir bibliotecas)](../../build/reference/nodefaultlib-ignore-libraries.md). para indicar al enlazador que omita las referencias de biblioteca en todos los archivos .obj.

Para obtener más información, vea [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).

Cuando se compila con **/Zl**, `_VC_NODEFAULTLIB` está definido.  Por ejemplo:

```
// vc_nodefaultlib.cpp
// compile with: /Zl
void Test() {
   #ifdef _VC_NODEFAULTLIB
      int i;
   #endif

   int i;   // C2086
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **avanzadas** página de propiedades.

1. Modificar el **omitir nombres de biblioteca predeterminada** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)