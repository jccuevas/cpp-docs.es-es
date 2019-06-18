---
title: /link (Pasar opciones al vinculador)
ms.date: 03/25/2019
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: 37743e855c933b6236b5e7a837db257f332a3037
ms.sourcegitcommit: bbaf65f8ed1af12828b38f8eacd24f934ac0e538
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "67155773"
---
# <a name="link-pass-options-to-linker"></a>/link (Pasar opciones al vinculador)

Pasa una o más opciones del vinculador al vinculador.

## <a name="syntax"></a>Sintaxis

> **/link** *linker-options*

## <a name="arguments"></a>Argumentos

*linker-options*<br/>
La opción del vinculador o las opciones que se pasarán al vinculador.

## <a name="remarks"></a>Comentarios

El **/link** opción y sus opciones del vinculador deben aparecer detrás de los nombres de archivo y las opciones de CL. Se requiere un espacio entre **/link** y las opciones del vinculador. Para obtener más información, consulte [referencia de vinculador MSVC](linking.md).

## <a name="example"></a>Ejemplo

Esta línea de comandos de ejemplo compila *hello.cpp* y lo vincula al archivo de objeto existente *there.obj*. A continuación, pasa adicional **/VERSION** comando al vinculador:

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

Normalmente, el IDE envía comandos independientes para compilar y vincular el código. Puede establecer las opciones del vinculador en sus páginas de propiedades del proyecto.

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** carpeta.

1. Modificar una o varias propiedades. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- No se puede cambiar esta opción del compilador mediante programación.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
