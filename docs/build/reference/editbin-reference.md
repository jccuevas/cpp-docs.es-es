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
ms.openlocfilehash: 266347de063b4e050cb032aa2d8d74e7934b8081
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328348"
---
# <a name="editbin-reference"></a>Referencia de EDITBIN

El Editor de archivos binarios de Microsoft COFF (EDITBIN. EXE) modifica los archivos binarios de formato de archivo de objeto común (COFF). Puede utilizar EDITBIN para modificar archivos de objetos, archivos ejecutables y bibliotecas de vínculos dinámicos (DLL).

> [!NOTE]
> Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

EDITBIN no está disponible para su uso en archivos generados con la opción del compilador [/GL.](gl-whole-program-optimization.md) Cualquier modificación de archivos binarios producidas con /GL tendrá que lograrse mediante la recompilación y vinculación.

- [Línea de comandos EDITBIN](editbin-command-line.md)

- [Opciones EDITBIN](editbin-options.md)

## <a name="see-also"></a>Consulte también

[Herramientas de compilación de MSVC adicionales](c-cpp-build-tools.md)
