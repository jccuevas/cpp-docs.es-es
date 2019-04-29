---
title: /SECTION (Especificar los atributos de la sección)
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 8fb73043c9c185adee0859bb81098eab022430c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318568"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Especificar los atributos de la sección)

> **/SECTION:**_name_,[[**!**]{**DEKPRSW**}][**,ALIGN=**_number_]

## <a name="remarks"></a>Comentarios

El **/SECTION** opción cambia los atributos de una sección reemplazando los atributos establecidos cuando se compiló el archivo .obj para la sección.

Un *sección* en un archivo ejecutable portable (PE) el archivo es un bloque de memoria que contiene el código o datos contiguo con nombre. Algunas secciones contienen código o datos que el programa declara y usa directamente, mientras que otras secciones de datos se crean automáticamente por el Administrador de biblioteca (lib.exe) y del vinculador y contienen información vital para el sistema operativo. Para obtener más información, consulte [formato PE](/windows/desktop/Debug/pe-format).

Especifique un signo de dos puntos (:) y una sección *nombre*. El *nombre* distingue mayúsculas de minúsculas.

No utilice los siguientes nombres, como que entren en conflicto con los nombres estándar. Por ejemplo, .sdata se utiliza en las plataformas RISC:

- .arch

- .bss

- .data

- .edata

- .idata

- .pdata

- .rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .text

- .xdata

Especifique uno o varios atributos de la sección. Los caracteres de atributo, que se muestran a continuación, no distinguen mayúsculas de minúsculas. Debe especificar todos los atributos que desea que la sección tener; hace que un carácter de atributo se omite ese bit del atributo se puede desactivar. Si no se especifica R, W o E, existente lectura, escritura o estado ejecutable permanece sin cambios.

Para invalidar un atributo, preceden su carácter con un signo de exclamación (!). Los significados de los caracteres del atributo se muestran en esta tabla:

|Carácter|Atributo|Significado|
|---------------|---------------|-------------|
|E|Ejecutar|La sección es ejecutable|
|R|Leer|Permite operaciones de lectura de datos|
|X|Write|Permite que las operaciones de escritura en datos|
|S|Shared|Comparte la sección entre todos los procesos que cargan la imagen|
|D|Puede descartar|Marca la sección como no descartable|
|K|Puede almacenar en caché|Marca la sección como no almacenable en caché|
|P|Paginable|Marca la sección como no paginable|

K y P no es habituales en que se usan los indicadores de sección que se corresponden con ellos en el sentido negativo. Si se especifica uno de ellos en la sección .text utilizando el **Text, K** opción, no hay ninguna diferencia en los indicadores de sección al ejecutar [DUMPBIN](dumpbin-options.md) con el [/HEADERS](headers.md)opción; la sección ya implícitamente se almacenó en caché. Para quitar el valor predeterminado, especifique **Text,! K** en su lugar. DUMPBIN revela las características de sección, incluidos "No almacenar en caché."

Una sección en el archivo PE que no tiene E, R o W establecido es probablemente no es válida.

El **ALIGN =**_número_ argumento le permite especificar un valor de alineación de una sección concreta. El _número_ argumento está en bytes y debe ser una potencia de dos. Consulte [/alinear](align-section-alignment.md) para obtener más información.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Elija la **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Especifique la opción en el **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
