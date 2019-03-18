---
title: /NODEFAULTLIB (Omitir bibliotecas)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
ms.openlocfilehash: cacc1ef312065da5d6e62ddba1040e87fae9d709
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807460"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Omitir bibliotecas)

```
/NODEFAULTLIB[:library]
```

## <a name="arguments"></a>Argumentos

*library*<br/>
Una biblioteca que desee al enlazador que omita al resolver referencias externas.

## <a name="remarks"></a>Comentarios

La opción /NODEFAULTLIB indica al vinculador que quite una o más bibliotecas predeterminadas de la lista de bibliotecas que realiza búsquedas al resolver referencias externas.

Para crear un archivo .obj que no contiene referencias a las bibliotecas predeterminadas, use [/Zl (Omit Default Library Name)](zl-omit-default-library-name.md).

De forma predeterminada, esta opción quitará todas las bibliotecas predeterminadas de la lista de bibliotecas que realiza búsquedas al resolver referencias externas. El elemento opcional *biblioteca* parámetro le permite quitar una biblioteca especificada o bibliotecas de la lista de bibliotecas que realiza búsquedas al resolver referencias externas. Especificar una opción/NODEFAULTLIB para cada biblioteca que desea excluir.

El vinculador resuelve las referencias a definiciones externas buscando en primer lugar en las bibliotecas que se especifiquen explícitamente, a continuación, en las bibliotecas especificadas con la opción DEFAULTLIB y, a continuación, en las bibliotecas predeterminadas mencionadas en los archivos .obj.

/ NODEFAULTLIB:*biblioteca* invalida [DEFAULTLIB:](defaultlib-specify-default-library.md)*biblioteca* cuando el mismo *biblioteca* nombre se especifica en ambos.

Si utiliza/NODEFAULTLIB, por ejemplo, para generar un programa sin la biblioteca de tiempo de ejecución de C, tendrá que usar también [/Entry](entry-entry-point-symbol.md) para especificar el punto de entrada (función) en el programa. Para obtener más información, vea [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **entrada**página de propiedades.

1. Seleccione el **omitir todas las bibliotecas predeterminadas** propiedad o especificar una lista de las bibliotecas que desea omitir en la **Omitir biblioteca específica** propiedad. El **línea de comandos** página de propiedades mostrará el efecto de los cambios que realice para estas propiedades.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
