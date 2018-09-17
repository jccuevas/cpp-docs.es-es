---
title: -Zm (especificar el límite de asignación de memoria de encabezado precompilado) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zm
dev_langs:
- C++
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9dfd1b0525991f81736af571d2c450e0c12edfc4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702738"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (Especificar el límite de asignación de memoria del encabezado precompilado)

Determina la cantidad de memoria que el compilador asigna para construir encabezados precompilados.

## <a name="syntax"></a>Sintaxis

```
/Zmfactor
```

## <a name="arguments"></a>Argumentos

*factor*<br/>
Factor de escala que determina la cantidad de memoria que el compilador utiliza para construir encabezados precompilados.

El *factor* argumento es un porcentaje del tamaño predeterminado de un búfer de trabajo definido por el compilador. El valor predeterminado de *factor* es 100 (porcentaje), pero puede especificar cantidades mayores o menores.

## <a name="remarks"></a>Comentarios

En versiones anteriores de Visual C++, el compilador utilizaba varios montones discretos, cada uno con un límite finito. Actualmente, el compilador aumenta dinámicamente los montones según sea necesario hasta un límite de tamaño de montón total, y solo requiere un búfer de tamaño fijo para construir los encabezados precompilados. Por lo tanto, el **/Zm** es raro tener la opción del compilador.

Si el compilador se ejecuta fuera del espacio de montón y emite el [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) recibe un mensaje de error cuando se usa el **/Zm** opción del compilador, es posible que haya reservado demasiada memoria. Considere la posibilidad de quitar el **/Zm** opción. Si el compilador emite la [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) mensaje de error, acompañado de un [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) mensaje especifica el *factor* argumento que se usará al volver a compilar mediante el uso de la **/Zm** opción del compilador.

La tabla siguiente muestra cómo el *factor* argumento afecta el límite de asignación de memoria si asume el tamaño del búfer de encabezado precompilado predeterminado es 75 MB.

|Valor de *factor*|Límite de asignación de memoria|
|-----------------------|-----------------------------|
|10|7.5 MB|
|100|75 MB|
|200|150 MB|
|1000|750 MB|
|2000|1.500 MB|

## <a name="other-ways-to-set-the-memory-allocation-limit"></a>Otras maneras de establecer el límite de la asignación de memoria

#### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer la opción /Zm del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. En el panel de navegación, seleccione **propiedades de configuración**, **C o C++**, **línea de comandos**.

1. Escriba el **/Zm** opción del compilador en el **opciones adicionales** cuadro.

#### <a name="to-set-the-zm-compiler-option-programmatically"></a>Para establecer la opción /Zm del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)