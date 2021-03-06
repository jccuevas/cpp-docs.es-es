---
title: /ZW (Compilación de Windows en tiempo de ejecución)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
ms.openlocfilehash: 0808f66c4d4c4e99b3038ea18a1f71f4ebaca89a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446177"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (Compilación de Windows en tiempo de ejecución)

Compila el código para admitir Microsoft fuente C++ extensiones de componentes C++/CX para la creación de aplicaciones de plataforma Universal de Windows (UWP).

Cuando usas **/ZW** para compilar, especifique siempre **/EHsc** también.

## <a name="syntax"></a>Sintaxis

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>Argumentos

**nostdlib**<br/>
Indica que Platform.winmd, Windows.Foundation.winmd y otros archivos de metadatos de Windows (.winmd) predeterminados no se incluyen automáticamente en la compilación, En su lugar, debe usar el [/FU (nombre #using archivo)](fu-name-forced-hash-using-file.md) opción del compilador para especificar explícitamente los archivos de metadatos de Windows.

## <a name="remarks"></a>Comentarios

Al especificar el **/ZW** opción, el compilador admite estas características:

- Los archivos de metadatos necesarios, espacios de nombres, tipos de datos y funciones que la aplicación necesita para ejecutarse en el tiempo de ejecución de Windows.

- Automático: recuento de referencias de objetos de Windows Runtime y descarte de un objeto cuando su recuento de referencias llega a cero automático.

Dado que el enlazador incremental no admite los metadatos de Windows incluidos en los archivos .obj mediante la **/ZW** opción desusado [/Gm (habilitar recompilación mínima)](gm-enable-minimal-rebuild.md) opción no es compatible con **/ZW**.

Para obtener más información, consulte [referencia del lenguaje Visual C++](../../cppcx/visual-c-language-reference-c-cx.md).

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
