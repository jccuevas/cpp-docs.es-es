---
title: Referencia de EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: 45c2967a55e85ae31bb77bb2e8d50415eafbea46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293035"
---
# <a name="editbin-reference"></a>Referencia de EDITBIN

El Editor de archivos de Microsoft COFF Binary (EDITBIN. (EXE) modifica los archivos binarios de formato de archivo de objeto común (COFF). Puede utilizar EDITBIN para modificar archivos de objetos, archivos ejecutables y bibliotecas de vínculos dinámicos (DLL).

> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

EDITBIN no está disponible para su uso en los archivos producidos con la [/GL](gl-whole-program-optimization.md) opción del compilador. Las modificaciones en los archivos binarios generados con/GL tendrán que se logra volver a compilar y vincular.

- [Línea de comandos EDITBIN](editbin-command-line.md)

- [Opciones de EDITBIN](editbin-options.md)

## <a name="see-also"></a>Vea también

[Herramientas de generación MSVC adicionales](c-cpp-build-tools.md)
