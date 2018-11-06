---
title: /F (Establecer el tamaño de la pila)
ms.date: 11/04/2016
f1_keywords:
- /f
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
ms.openlocfilehash: 69d26a4e4634ea60457d75bc97d2266036d11e10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525533"
---
# <a name="f-set-stack-size"></a>/F (Establecer el tamaño de la pila)

Establece el tamaño de pila del programa en bytes.

## <a name="syntax"></a>Sintaxis

> **/F** *número*

## <a name="arguments"></a>Argumentos

*Número*<br/>
El tamaño de pila en bytes.

## <a name="remarks"></a>Comentarios

Sin esta opción, el tamaño de pila predeterminado es 1 MB. El *número* argumento puede ser en notación de lenguaje de C o decimal. El argumento puede oscilar entre 1 y el tamaño de pila máximo aceptado por el vinculador. El vinculador se redondea el valor especificado a los 4 bytes más cercanos. El espacio entre **/F** y *número* es opcional.

Es posible que deba aumentar el tamaño de pila si el programa obtiene mensajes de desbordamiento de pila.

También puede establecer el tamaño de pila:

- Mediante el **/pila** opción del vinculador. Para obtener más información, consulte [/pila](../../build/reference/stack.md).

- En el archivo .exe, mediante EDITBIN. Para obtener más información, consulte [referencia de EDITBIN](../../build/reference/editbin-reference.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)