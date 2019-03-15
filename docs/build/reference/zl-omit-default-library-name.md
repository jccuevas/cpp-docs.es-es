---
title: /Zl (Omitir nombres de biblioteca predeterminada)
ms.date: 11/04/2016
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
ms.openlocfilehash: cb8083d874abe17add1d27096ebce143d03a04cf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809592"
---
# <a name="zl-omit-default-library-name"></a>/Zl (Omitir nombres de biblioteca predeterminada)

Omite el nombre de biblioteca predeterminado en tiempo de ejecución de C desde el archivo .obj. De forma predeterminada, el compilador sitúa el nombre de la biblioteca en el archivo .obj para dirigir el enlazador hacia la biblioteca correcta.

## <a name="syntax"></a>Sintaxis

```
/Zl
```

## <a name="remarks"></a>Comentarios

Para obtener más información acerca de la biblioteca predeterminada, vea [utilizar la biblioteca en tiempo de ejecución](md-mt-ld-use-run-time-library.md).

Puede usar **/Zl** para compilar archivos .obj que piense incluir en una biblioteca. Aunque si se omite el nombre de la biblioteca guarda sólo una pequeña cantidad de espacio para un solo archivo .obj, el ahorro de espacio total es significativo en una biblioteca que contiene muchos módulos de objeto.

Esta opción es una opción avanzada. Al establecer esta opción quita cierta compatibilidad de biblioteca en tiempo de ejecución de C que puede ser necesario para la aplicación, lo que produce errores en tiempo de vínculo si la aplicación depende de esta compatibilidad. Si usa esta opción debe proporcionar los componentes necesarios de alguna otra manera.

Use [/NODEFAULTLIB (Omitir bibliotecas)](nodefaultlib-ignore-libraries.md). para indicar al enlazador que omita las referencias de biblioteca en todos los archivos .obj.

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **avanzadas** página de propiedades.

1. Modificar el **omitir nombres de biblioteca predeterminada** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
