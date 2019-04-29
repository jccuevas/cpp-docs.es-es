---
title: /DELAYSIGN (Firmar parcialmente un ensamblado)
ms.date: 11/04/2016
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
ms.openlocfilehash: 65585b856627ad9fda5a8f8bfad6ad81fef0f81c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293841"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (Firmar parcialmente un ensamblado)

```
/DELAYSIGN[:NO]
```

## <a name="arguments"></a>Argumentos

**NO**<br/>
Especifica que el ensamblado no se debería firmar parcialmente.

## <a name="remarks"></a>Comentarios

Use **/DELAYSIGN** si solo desea colocar la clave pública del ensamblado. El valor predeterminado es **/delaysign: no**.

El **/DELAYSIGN** opción no tiene ningún efecto a menos que se usa con [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) o [/keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md).

Cuando se solicita un ensamblado totalmente firmado, el compilador genera un valor hash para el archivo que contiene el manifiesto (metadatos del ensamblado) y firma dicho valor mediante la clave privada. La firma digital resultante se almacena en el archivo que contiene el manifiesto. Cuando se retrasa la firma de un ensamblado, el vinculador no de proceso y almacena la firma, pero reserva espacio en el archivo para que la firma se puede agregar más adelante.

Por ejemplo, mediante **/DELAYSIGN** evaluadores podrán colocar el ensamblado en la caché global. Después de probar, puede firmar completamente el ensamblado colocando la clave privada en el ensamblado.

Consulte [ensamblados de nombre seguro (firma de ensamblados) (C++ / c++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) y [Delay Signing an Assembly](/dotnet/framework/app-domains/delay-sign-assembly) para obtener más información sobre cómo firmar un ensamblado.

Otras opciones del vinculador que afectan a la generación de ensamblado son:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
