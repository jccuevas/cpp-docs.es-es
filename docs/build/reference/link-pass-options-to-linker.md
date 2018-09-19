---
title: -link (pasar opciones al vinculador) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /link
dev_langs:
- C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 663407e4948ebc4e3c0a1676c44e8d2b4bd53fcc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704124"
---
# <a name="link-pass-options-to-linker"></a>/link (Pasar opciones al vinculador)

Pasa una o más opciones del vinculador al vinculador.

## <a name="syntax"></a>Sintaxis

```
/link linkeroptions
```

## <a name="arguments"></a>Argumentos

*linkeroptions*<br/>
La opción del vinculador o las opciones que se pasarán al vinculador.

## <a name="remarks"></a>Comentarios

El **/link** opción y sus opciones del vinculador deben aparecer detrás de los nombres de archivo y las opciones de CL. Se requiere un espacio entre **/link** y `linkeroptions`. Para obtener más información, consulte [opciones de configuración del vinculador](../../build/reference/setting-linker-options.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en una página de propiedades del enlazador.

1. Modificar una o varias propiedades.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- No se puede cambiar esta opción del compilador mediante programación.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)