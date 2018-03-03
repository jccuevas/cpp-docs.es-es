---
title: -ORDEN (colocar las funciones en orden) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2264296d288f9105a59c0ac5099c1dedef55ee2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="order-put-functions-in-order"></a>/ORDER (Colocar las funciones en orden)

Especificar el orden de los vínculos de funciones de forma independiente empaquetados (COMDAT).

## <a name="syntax"></a>Sintaxis

>/ ORDENAR: @*nombre de archivo*

### <a name="parameters"></a>Parámetros

*filename*  
Un archivo de texto que especifica el orden de los vínculos de las funciones COMDAT.

## <a name="remarks"></a>Comentarios

El **/orden** opción del compilador permite optimizar el comportamiento del programa paginación mediante la agrupación de una función junto con las funciones que se llama. También puede agrupar funciones llama con frecuencia. Estas técnicas, conocidas como *ajuste del intercambio* o *optimización paginación*, aumentar la probabilidad de que una función llamada está en la memoria cuando es necesario y no tiene que ser paginada desde el disco.

Cuando se compila el código fuente en un archivo de objeto, puede indicar al compilador que coloque cada función tiene su propia sección, denominado un *COMDAT*, mediante el uso de la [/Gy (habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md) compilador opción. El **/orden** opción del vinculador indica al vinculador que coloca COMDAT en la imagen ejecutable en el orden que especifique.

Para especificar el orden COMDAT, cree un *archivo de respuesta*, un archivo de texto que enumera cada COMDAT por su nombre, uno por línea, en el orden en que desea colocar el vinculador. Pase el nombre de este archivo como la *filename* parámetro de la **/orden** opción. Para las funciones de C++, el nombre de un COMDAT es el formato representativo del nombre de función. Use el nombre no representativo para las funciones de C, `main`, y para las funciones de C++ declaradas como `extern "C"`. Nombres de función y nombres representativos distinguen mayúsculas de minúsculas. Para obtener más información sobre nombres representativos, vea [nombres representativos](../../build/reference/decorated-names.md). 

Para buscar los nombres representativos de su comdat, use la [DUMPBIN](../../build/reference/dumpbin-reference.md) la herramienta [/símbolos](../../build/reference/symbols.md) opción en el archivo de objeto. El vinculador antepone automáticamente un carácter de subrayado (\_) a la función en la respuesta los nombres de archivo a menos que el nombre empieza con un signo de interrogación (?) o una arroba (@). Por ejemplo, si un archivo de código fuente, example.cpp, contiene funciones `int cpp_func(int)`, `extern "C" int c_func(int)` y `int main(void)`, el comando `DUMPBIN /SYMBOLS example.obj` enumera estos nombres representativos:

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

En este caso, especifique los nombres como `?cpp_func@@YAHH@Z`, `c_func`, y `main` en el archivo de respuesta.

Si más de un **/orden** opción aparece en las opciones del vinculador, la penúltima especificada surte efecto.

El **/orden** opción deshabilita la vinculación incremental. Es posible que vea Advertencia del vinculador [LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md) cuando se especifica esta opción si está habilitada la vinculación incremental, o si ha especificado el [/ZI (Incremental PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) opción del compilador. Para silenciar esta advertencia, puede usar el [/incremental: no](../../build/reference/incremental-link-incrementally.md) opción del vinculador para desactivar la vinculación incremental y usar el [/ZI (generar PDB)](../../build/reference/z7-zi-zi-debug-information-format.md) opción del compilador para generar un archivo PDB sin vinculación incremental.

> [!NOTE]
> VÍNCULO no puede ordenar las funciones estáticas porque los nombres de función estática no son nombres de símbolos públicos. Cuando **/orden** se especifica, advertencia del vinculador [LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md) se genera para cada símbolo en el archivo de respuesta de pedido que es estático o no se encuentra.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  

1. En **propiedades de configuración**, abra **vinculador** y, a continuación, elija la **optimización** página de propiedades.

1. Modificar el **orden función** propiedad que se va a contener el nombre del archivo de respuesta.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)