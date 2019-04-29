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
ms.openlocfilehash: ef81a6617df811660506c08434f3b65e29155794
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290688"
---
# <a name="link-pass-options-to-linker"></a>/link (Pasar opciones al vinculador)

Pasa una o más opciones del vinculador al vinculador.

## <a name="syntax"></a>Sintaxis

> **/link** *linker-options*

## <a name="arguments"></a>Argumentos

*linker-options*<br/>
La opción del vinculador o las opciones que se pasarán al vinculador.

## <a name="remarks"></a>Comentarios

El **/link** opción y sus opciones del vinculador deben aparecer detrás de los nombres de archivo y las opciones de CL. Se requiere un espacio entre **/link** y `linkeroptions`. Para obtener más información, consulte [referencia de vinculador MSVC](linking.md).

## <a name="example"></a>Ejemplo

Esta línea de comandos de ejemplo compila *hello.cpp* y lo vincula al archivo de objeto existente *there.obj*. A continuación, pasa adicional **/VERSION** comando al vinculador:

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

Normalmente, el IDE envía comandos independientes para compilar y vincular el código. Puede establecer las opciones del vinculador en sus páginas de propiedades del proyecto.

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** carpeta.

1. Modificar una o varias propiedades. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- No se puede cambiar esta opción del compilador mediante programación.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
