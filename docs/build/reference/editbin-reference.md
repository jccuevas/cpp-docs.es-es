---
title: Referencia de EDITBIN | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 809d1d4f25611b2310d651702f01e1e98888ad4a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699952"
---
# <a name="editbin-reference"></a>Referencia de EDITBIN

El Editor de archivos de Microsoft COFF Binary (EDITBIN. (EXE) modifica los archivos binarios de formato de archivo de objeto común (COFF). Puede utilizar EDITBIN para modificar archivos de objetos, archivos ejecutables y bibliotecas de vínculos dinámicos (DLL).

> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

EDITBIN no está disponible para su uso en los archivos producidos con la [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador. Las modificaciones en los archivos binarios generados con/GL tendrán que se logra volver a compilar y vincular.

- [Línea de comandos EDITBIN](../../build/reference/editbin-command-line.md)

- [Opciones de EDITBIN](../../build/reference/editbin-options.md)

## <a name="see-also"></a>Vea también

[Herramientas de compilación de C/C++](../../build/reference/c-cpp-build-tools.md)