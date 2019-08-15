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
ms.openlocfilehash: 0a52e9c9dcd53b01f17dc36825732b34771c75bb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492626"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Especificar los atributos de la sección)

> **/Section:** _nombre_, [[ **!** ] {**DEKPRSW**}] [ **, Align =** _número_]

## <a name="remarks"></a>Comentarios

La opción **/section** cambia los atributos de una sección, invalidando los atributos establecidos cuando se compiló el archivo. obj para la sección.

Una *sección* de un archivo portable ejecutable (PE) es un bloque de memoria contiguo con nombre que contiene código o datos. Algunas secciones contienen código o datos que el programa ha declarado y utiliza directamente, mientras que las demás secciones de datos las crea el enlazador y el administrador de bibliotecas (lib. exe) y contienen información fundamental para el sistema operativo. Para obtener más información, consulte [formato PE](/windows/win32/Debug/pe-format).

Especifique un signo de dos puntos (:) y un *nombre*de sección. El *nombre* distingue mayúsculas de minúsculas.

No use los nombres siguientes, ya que entran en conflicto con los nombres estándar. Por ejemplo, se usa. sdata en plataformas RISC:

- . Arch

- . BSS

- .data

- .edata

- .idata

- . pdata

- . rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- . Text

- .xdata

Especifique uno o más atributos para la sección. Los caracteres de atributo, que se enumeran a continuación, no distinguen mayúsculas de minúsculas. Debe especificar todos los atributos que desea que tenga la sección; un carácter de atributo omitido hace que el bit del atributo esté desactivado. Si no especifica R, W o E, el estado de lectura, escritura o ejecutable existente permanece inalterado.

Para negar un atributo, anteponga un signo de exclamación (!) a su carácter. Los significados de los caracteres de atributo se muestran en esta tabla:

|Carácter|Atributo|Significado|
|---------------|---------------|-------------|
|E|Ejecutar|La sección es ejecutable|
|R|Lectura|Permite operaciones de lectura en los datos|
|W|Escritura|Permite operaciones de escritura en datos|
|S|Shared|Comparte la sección entre todos los procesos que cargan la imagen.|
|D|Descartable|Marca la sección como descartable|
|K|Almacenable en caché|Marca la sección como no almacenable en caché|
|P|Paginable|Marca la sección como no paginable|

K y P son inusuales en que las marcas de la sección que se corresponden con ellas se usan en el sentido negativo. Si especifica uno de ellos en la sección. Text mediante la opción **/section:. Text, K** , no hay ninguna diferencia en las marcas de sección al ejecutar [dumpbin](dumpbin-options.md) con la opción [/headers](headers.md) . la sección ya se almacenó en caché de forma implícita. Para quitar el valor predeterminado, especifique **/section:. Text,! K** en su lugar. DUMPBIN revela características de la sección, incluido "no almacenado en caché".

Una sección del archivo PE que no tenga establecido E, R o W probablemente no sea válida.

El argumento **align =** _Number_ permite especificar un valor de alineación para una sección determinada. El argumento _Number_ está en bytes y debe ser una potencia de dos. Vea [/align](align-section-alignment.md) para obtener más información.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Elija la página de propiedades**línea de comandos** del**vinculador** > de **propiedades** > de configuración.

1. Escriba la opción en el cuadro **opciones adicionales** . Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
