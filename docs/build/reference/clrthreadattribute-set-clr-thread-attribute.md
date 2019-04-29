---
title: /CLRTHREADATTRIBUTE (Establecer el atributo de subproceso de CLR)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
ms.openlocfilehash: ad07c84a5c470cd5fa1ac10ff6d2baed5c35c025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272473"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Establecer el atributo de subproceso de CLR)

Especificar explícitamente el atributo de subprocesamiento del punto de entrada del programa CLR.

## <a name="syntax"></a>Sintaxis

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>Parámetros

**MTA**<br/>
Se aplica el atributo MTAThreadAttribute al punto de entrada del programa.

**NINGUNO**<br/>
Igual que el no especificar/CLRTHREADATTRIBUTE.  Permite que Common Language Runtime (CLR) establezca el atributo de subprocesamiento predeterminado.

**STA**<br/>
Se aplica el atributo STAThreadAttribute al punto de entrada del programa.

## <a name="remarks"></a>Comentarios

Establecer el atributo thread solo es válido cuando se genera un .exe, ya que afecta el punto de entrada del subproceso principal.

Si usa el punto de entrada predeterminado (main o wmain, por ejemplo) Especifique el modelo de subprocesos mediante/CLRTHREADATTRIBUTE o colocando el atributo de subprocesamiento (STAThreadAttribute o MTAThreadAttribute) en la función de entrada predeterminada.

Si usa un punto de entrada no predeterminado, especifique el modelo de subprocesos mediante/CLRTHREADATTRIBUTE o colocando el subprocesamiento atributo en la función de entrada no predeterminada y, a continuación, especifique el punto de entrada no predeterminada con [/Entry](entry-entry-point-symbol.md) .

Si el modelo de subprocesos especificado en el código fuente no está de acuerdo con el modelo de subprocesos especificado con/CLRTHREADATTRIBUTE, el vinculador omitirá/CLRTHREADATTRIBUTE y aplicar el modelo de subprocesos especificado en el código fuente.

Será necesario que utilice el subprocesamiento único, por ejemplo, si su programa de CLR hospeda un objeto COM que usa el subprocesamiento único.  Si el programa de CLR usa el subprocesamiento múltiple, no se puede hospedar un objeto COM que usa el subprocesamiento único.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **el atributo de subproceso de CLR** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
