---
title: -MANIFESTDEPENDENCY (especificar las dependencias del manifiesto) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
dev_langs:
- C++
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b82bd32bec0e665f815563ccea2ee05f6ae5172
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315423"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Especificar las dependencias del manifiesto)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Comentarios

/MANIFESTDEPENDENCY le permite especificar atributos que se colocarán en el \<dependencia > sección del archivo de manifiesto.

Consulte [/manifest (crear Side-by-Side manifiesto del ensamblado)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) para obtener información sobre cómo crear un archivo de manifiesto.

Para obtener más información sobre la \<dependencia > sección del archivo de manifiesto, vea [archivos de configuración del publicador](/windows/desktop/SbsCs/publisher-configuration-files).

/ Información MANIFESTDEPENDENCY puede pasarse al vinculador en uno de dos maneras:

- Directamente en la línea de comandos (o en un archivo de respuesta) con/MANIFESTDEPENDENCY.

- A través de la [comentario](../../preprocessor/comment-c-cpp.md) pragma.

El ejemplo siguiente muestra un comentario/MANIFESTDEPENDENCY pasado a través de la directiva pragma,

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

lo que da como resultado la siguiente entrada en el archivo de manifiesto:

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Los mismos comentarios/MANIFESTDEPENDENCY pueden pasarse a la línea de comandos como sigue:

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

El vinculador recopilar comentarios/MANIFESTDEPENDENCY, eliminará las entradas duplicadas y, a continuación, agregue la cadena XML resultante al archivo de manifiesto.  Si el vinculador busca entradas en conflicto, el archivo de manifiesto estará dañado y se producirá un error de la aplicación iniciar (es posible que se agrega una entrada al registro de eventos, que indica el origen del error).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **archivo de manifiesto** página de propiedades.

1. Modificar el **dependencias de manifiesto adicionales** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)