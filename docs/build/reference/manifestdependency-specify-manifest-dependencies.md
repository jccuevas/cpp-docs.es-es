---
title: /MANIFESTDEPENDENCY (Especificar las dependencias del manifiesto)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: 43239efe70cc555d1a7e03c5d67e99e40ccd480e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492702"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Especificar las dependencias del manifiesto)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Comentarios

/MANIFESTDEPENDENCY le permite especificar los atributos que se colocarán \<en la sección de > de dependencia del archivo de manifiesto.

Vea [/manifest (crear el manifiesto del ensamblado en paralelo)](manifest-create-side-by-side-assembly-manifest.md) para obtener información sobre cómo crear un archivo de manifiesto.

Para obtener más información sobre \<la sección > de dependencia del archivo de manifiesto, consulte [archivos de configuración](/windows/win32/SbsCs/publisher-configuration-files)del publicador.

La información de/MANIFESTDEPENDENCY se puede pasar al enlazador de una de estas dos maneras:

- Directamente en la línea de comandos (o en un archivo de respuesta) con/MANIFESTDEPENDENCY.

- Mediante el pragma [comment](../../preprocessor/comment-c-cpp.md) .

En el ejemplo siguiente se muestra un comentario/MANIFESTDEPENDENCY pasado a través de pragma,

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

Esto da como resultado la siguiente entrada en el archivo de manifiesto:

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Los mismos comentarios/MANIFESTDEPENDENCY se pueden pasar en la línea de comandos de la siguiente manera:

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

El vinculador recopilará comentarios/MANIFESTDEPENDENCY, eliminará entradas duplicadas y, a continuación, agregará la cadena XML resultante al archivo de manifiesto.  Si el vinculador encuentra entradas en conflicto, el archivo de manifiesto se dañará y la aplicación no se iniciará (se puede Agregar una entrada al registro de eventos, lo que indica el origen del error).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **configuración** > del**archivo de manifiesto** del**enlazador** > .

1. Modifique la propiedad dependencias de **manifiesto adicionales** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
