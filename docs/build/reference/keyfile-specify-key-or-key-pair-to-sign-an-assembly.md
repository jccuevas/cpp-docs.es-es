---
title: /KEYFILE (Especificar una clave o par de claves para firmar un ensamblado)
ms.date: 11/04/2016
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
ms.openlocfilehash: d309390c1ac1a19d9d4a982908dbbbac0bd52714
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813778"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (Especificar una clave o par de claves para firmar un ensamblado)

```
/KEYFILE:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
Archivo que contiene la clave. Escriba la cadena entre comillas dobles ("") si contiene un espacio.

## <a name="remarks"></a>Comentarios

El vinculador inserta la clave pública en el manifiesto del ensamblado y, a continuación, firma el ensamblado final con la clave privada. Para generar un archivo de clave, escriba [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* en la línea de comandos. Un ensamblado firmado se dice que tiene un nombre seguro.

Si se compila con [/LN](ln-create-msil-module.md), el nombre del archivo de clave se mantiene en el módulo y se incorpora al ensamblado que se crea cuando se compila un ensamblado que incluye una referencia explícita al módulo, a través de [#using](../../preprocessor/hash-using-directive-cpp.md), o al vincular con [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md).

También puede pasar la información de cifrado al vinculador con [/keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md). Use [/DELAYSIGN](delaysign-partially-sign-an-assembly.md) si desea firmar parcialmente un ensamblado. Consulte [ensamblados de nombre seguro (firma de ensamblados) (C++ / c++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) para obtener más información sobre cómo firmar un ensamblado.

En caso de ambos **/keyfile** y **/keycontainer** se especifican (mediante una opción de línea de comandos o mediante un atributo personalizado), el vinculador probará primero el contenedor de claves. Si lo consigue, el ensamblado se firma con la información del contenedor de claves. Si el vinculador no encuentra el contenedor de claves, probará el archivo especificado con/keyfile. Si lo consigue, el ensamblado se firma con la información del archivo de clave y la información de la clave se instalará en el contenedor de claves (similar a sn -i) de modo que, en la próxima compilación, el contenedor de claves será válido.

Tenga en cuenta que un archivo de clave puede contener solo la clave pública.

Consulte [crear y utilizar ensamblados](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) para obtener más información sobre cómo firmar un ensamblado.

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

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
