---
title: /INCREMENTAL (Vincular de forma incremental)
ms.date: 11/04/2016
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
ms.openlocfilehash: 0ef6e8c7fed2c58e8fc2949a84483015bbc9d6bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642034"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (Vincular de forma incremental)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>Comentarios

Controla el modo en que el vinculador administra la vinculación incremental.

De manera predeterminada, el vinculador se ejecuta en modo incremental. Para reemplazar un vínculo incremental predeterminado, especifique /INCREMENTAL:NO.

Un programa vinculado de forma incremental es funcionalmente equivalente a un programa que esté vinculado de forma no incremental. Sin embargo, al estar preparados para posteriores vínculos incrementales, una biblioteca estática, ejecutable vinculado incrementalmente o el archivo de biblioteca de vínculos dinámicos:

- Es mayor que un programa vinculado de forma no incremental a causa del relleno del código y los datos. Relleno permite al vinculador aumentar el tamaño de las funciones y los datos sin volver a crear el archivo.

- Pueden contener códigos thunk de salto para controlar la reubicación de las funciones en direcciones nuevas.

   > [!NOTE]
   > Para asegurarse de que la compilación de lanzamiento final no contiene relleno ni códigos thunk, vincule el programa de manera no incremental.

Para vincular de forma incremental con independencia del valor predeterminado, especifique /INCREMENTAL. Cuando se selecciona esta opción, el vinculador emite una advertencia si no se puede vincular de forma incremental y, a continuación, vincula el programa de forma no incremental. Hay ciertas opciones y situaciones que invalidan la opción /INCREMENTAL.

La mayoría de los programas pueden vincularse de manera incremental. Sin embargo, algunos cambios son demasiado grandes y algunas opciones no son compatibles con la vinculación incremental. LINK realizará un vínculo completo si se especifica cualquiera de las opciones siguientes:

- No se selecciona la vinculación incremental (/INCREMENTAL:NO).

- Se selecciona /OPT:REF.

- Se selecciona /OPT:ICF.

- Se selecciona /OPT:LBR.

- Se selecciona /ORDER.

/INCREMENTAL está implícita cuando [/DEBUG](../../build/reference/debug-generate-debug-info.md) se especifica.

Asimismo, LINK realizará un vínculo completo si se da alguna de las situaciones siguientes:

- Falta el archivo de estado incremental (.ilk). (LINK crea un archivo .ilk nuevo en previsión de una vinculación incremental posterior).

- No se cuenta con permiso de escritura para el archivo .ilk. (LINK omite el archivo .ilk y forma no incremental.)

- Falta el archivo de salida .exe o .dll.

- Se ha modificado la marca de tiempo del archivo .ilk, .exe o .dll.

- Se ha modificado una opción de LINK. La mayoría de las opciones de LINK, si se cambian entre compilaciones, producen un vínculo completo.

- Se ha agregado u omitido un archivo objeto (.obj).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione la página de propiedades **General** .

1. Modificar el **habilitar vinculación Incremental** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)