---
title: /Section (especificar atributos de sección) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d9b0a724f0e9156c81db20bf283e4418dd2f22d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379528"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Especificar los atributos de la sección)

> **/ SECCIÓN:**_nombre_, [[**!**] {**DEKPRSW**}] [**, ALIGN =**_número_]

## <a name="remarks"></a>Comentarios

El **/SECTION** opción modifica los atributos de una sección, reemplazando los atributos establecidos cuando se compiló el archivo .obj para la sección.

A *sección* en un archivo ejecutable portable (PE) archivo es un bloque de memoria que contiene código o datos contiguo con nombre. Algunas secciones contienen código o datos que el programa declara y utiliza directamente, mientras que otras secciones de datos se crean para el vinculador y el Administrador de bibliotecas (lib.exe) y contienen información fundamental para el sistema operativo. Para obtener más información, consulte [formato PE](https://msdn.microsoft.com/library/windows/desktop/ms680547).

Especifique un signo de dos puntos (:) y una sección *nombre*. El *nombre* distingue mayúsculas de minúsculas.

No utilice los siguientes nombres, tal y como entran en conflicto con los nombres estándar. Por ejemplo, .sdata se utiliza en plataformas RISC:

- .arch

- BSS

- .Data

- .edata

- .IData

- .pdata

- rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- Text

- .XData

Especifique uno o más atributos de la sección. Los caracteres de atributo, que se muestran a continuación, no distinguen mayúsculas de minúsculas. Debe especificar todos los atributos que desea que la sección tener; el carácter de un atributo se omite hace bit del atributo se ha desactivado. Si no se especifica R, W o E, existente lectura, escritura o estado ejecutable permanece sin cambios.

Para invalidar un atributo, preceden su carácter con un signo de exclamación (!). Los significados de los caracteres de atributo se muestran en esta tabla:

|Carácter|Atributo|Significado|
|---------------|---------------|-------------|
|E|Ejecutar|La sección es ejecutable|
|R|Leer|Permite operaciones de lectura en datos|
|X|Write|Permite operaciones de escritura en los datos|
|S|Compartido|Comparte la sección entre todos los procesos que cargan la imagen|
|D|Descartable|Marca la sección como no descartable|
|K|Almacenable en caché|Marca la sección como no almacenable en caché|
|P|Paginable|Marca la sección como no paginable|

K y P tienen poco habitual en que se utilizan los indicadores de sección que les corresponden en un sentido negativo. Si se especifica uno de ellos en la sección .text mediante la **Text, K** opción, no hay ninguna diferencia en los indicadores de sección al ejecutar [DUMPBIN](../../build/reference/dumpbin-options.md) con el [/HEADERS](../../build/reference/headers.md)opción; la sección ya implícitamente se almacenó en caché. Para quitar el valor predeterminado, especifique **Text,! K** en su lugar. DUMPBIN revela las características de sección, incluyendo "No almacenado en caché."

Una sección del archivo PE que no tenga E, R o W establecido es probablemente no será válida.

El **ALIGN =**_número_ argumento le permite especificar un valor de alineación para una sección concreta. El _número_ argumento está en bytes y debe ser una potencia de dos. Vea [/alinear](../../build/reference/align-section-alignment.md) para obtener más información.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Elija la **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba la opción en la **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)  
