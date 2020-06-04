---
title: /LN (Crear un módulo MSIL)
ms.date: 11/04/2016
f1_keywords:
- /LN
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
ms.openlocfilehash: 2dbd5ae5ddf802185912c49caf37aa61c6a7d4c3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446264"
---
# <a name="ln-create-msil-module"></a>/LN (Crear un módulo MSIL)

Especifica que no se debe insertar un manifiesto de ensamblado en el archivo de salida.

## <a name="syntax"></a>Sintaxis

```
/LN
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, **/LN** no está en vigor (un manifiesto del ensamblado se inserta en el archivo de salida).

Cuando **/LN** sirve, uno de los [/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md) también se deben utilizar las opciones.

Un programa administrado que no tiene metadatos de ensamblado en el manifiesto se denomina un módulo. Si se compila con [/c (compilar sin vincular)](c-compile-without-linking.md) y **/LN**, especifique [/NOASSEMBLY (crear un módulo MSIL)](noassembly-create-a-msil-module.md) en la fase del enlazador para crear el archivo de salida.

Desea crear módulos si desea adoptar un enfoque basado en componentes para generar ensamblados.  Es decir, puede crear tipos y compilarlas en módulos.  A continuación, puede generar un ensamblado de uno o varios módulos.  Para obtener más información sobre cómo crear ensamblados de los módulos, consulte [archivos .netmodule como entrada del vinculador](netmodule-files-as-linker-input.md) o [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

La extensión de archivo predeterminado para un módulo es. netmodule.

En versiones anteriores a Visual Studio 2005, se creó un módulo con **/CLR: noAssembly**.

El vinculador MSVC acepta archivos .netmodule como entrada y el archivo de salida generado por el vinculador será un ensamblado o .netmodule sin ninguna dependencia de tiempo de ejecución en cualquiera de los archivos .netmodule que se utilizaron como entrada del vinculador.  Para más información, consulte [Archivos .netmodule como entrada del vinculador](netmodule-files-as-linker-input.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

- Especificar [/NOASSEMBLY (crear un módulo MSIL)](noassembly-create-a-msil-module.md) en la fase del enlazador para crear el archivo de salida.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- No se puede cambiar esta opción del compilador mediante programación.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
