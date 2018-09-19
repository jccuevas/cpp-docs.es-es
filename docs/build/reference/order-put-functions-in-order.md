---
title: -ORDER (colocar las funciones en orden) | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
dev_langs:
- C++
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8ea4df02e87a64d70ce773ed35d1a3cb0509f8b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717799"
---
# <a name="order-put-functions-in-order"></a>/ORDER (Colocar las funciones en orden)

Especificar el orden de vínculo de funciones de por separado empaquetadas (COMDAT).

## <a name="syntax"></a>Sintaxis

> **/ ORDER:\@**<em>nombre de archivo</em>

### <a name="parameters"></a>Parámetros

*filename*<br/>
Un archivo de texto que especifica el orden de vínculos de las funciones COMDAT.

## <a name="remarks"></a>Comentarios

El **/Order** opción del compilador permite optimizar el comportamiento de paginación del programa mediante la agrupación de una función junto con las funciones a las que llama. También puede agrupar las funciones se llama con frecuencia juntos. Estas técnicas, conocidas como *ajuste del intercambio* o *optimización paginación*, aumentar la probabilidad de que una función llamada está en la memoria cuando es necesario y no tiene que ser paginada desde el disco.

Al compilar el código fuente en un archivo de objeto, puede indicar al compilador que coloque cada función tiene su propia sección, se llama a un *COMDAT*, mediante el uso de la [/Gy (habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md) compilador opción. El **/Order** opción del vinculador indica al vinculador coloque COMDAT en la imagen ejecutable en el orden que especifique.

Para especificar el orden COMDAT, cree un *archivo de respuesta*, un archivo de texto que enumera cada COMDAT por nombre, uno por línea, en el orden en que desea colocar el vinculador. Pase el nombre de este archivo como el *filename* parámetro de la **/Order** opción. Para las funciones de C++, el nombre de un COMDAT es el formato representativo del nombre de función. Use el nombre no representativo para las funciones de C, `main`, y para las funciones de C++ declaradas como `extern "C"`. Los nombres de función y los nombres representativos distinguen mayúsculas de minúsculas. Para obtener más información sobre los nombres representativos, vea [nombres representativos](../../build/reference/decorated-names.md).

Para buscar los nombres representativos de los comdat, use el [DUMPBIN](../../build/reference/dumpbin-reference.md) la herramienta [/símbolos](../../build/reference/symbols.md) opción en el archivo de objeto. El vinculador antepone automáticamente un carácter de subrayado (**\_**) a la función en la respuesta de los nombres de archivo a menos que el nombre comienza con un signo de interrogación (**?**) o signo de arroba ( **\@**). Por ejemplo, si un archivo de código fuente, example.cpp, contiene funciones `int cpp_func(int)`, `extern "C" int c_func(int)` y `int main(void)`, el comando `DUMPBIN /SYMBOLS example.obj` enumera estos nombres representativos:

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

En este caso, especifique los nombres como `?cpp_func@@YAHH@Z`, `c_func`, y `main` en el archivo de respuesta.

Si más de un **/Order** opción aparece en las opciones del vinculador, la última de ellas especifica surte efecto.

El **/Order** opción deshabilita la vinculación incremental. Es posible que vea la advertencia del vinculador [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) cuando se especifica esta opción si la vinculación incremental está habilitada o si ha especificado el [/ZI (Incremental PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) opción del compilador. Para silenciar esta advertencia, puede usar el [/incremental: no](../../build/reference/incremental-link-incrementally.md) opción del vinculador para desactivar la vinculación incremental y usar el [/ZI (generar PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) opción del compilador para generar un archivo PDB sin vinculación incremental.

> [!NOTE]
> VÍNCULO no puede ordenar las funciones estáticas porque los nombres de función estático no son nombres de símbolos públicos. Cuando **/Order** se especifica, advertencia del vinculador [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) se genera para cada símbolo en el archivo de respuesta de pedido es estático o no se encuentra.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **optimización** página de propiedades.

1. Modificar el **orden de función** propiedad que se va a contener el nombre del archivo de respuesta.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)