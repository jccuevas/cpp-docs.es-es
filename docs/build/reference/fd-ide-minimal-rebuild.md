---
title: /FD (Recompilación mínima de IDE)
ms.date: 04/08/2019
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 896adcb97a259e6714cf23241424841456371491
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439809"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Recompilación mínima de IDE)

**/FD** solo se expone a los usuarios en la página de propiedades [línea](command-line-property-pages.md) de C++ comandos del cuadro de diálogo **páginas de propiedades** de un proyecto. Está disponible solo si la opción [/GM (habilitar recompilación mínima)](gm-enable-minimal-rebuild.md) en desuso y desusada de forma predeterminada no está seleccionada. **/FD** no tiene ningún efecto que no sea del entorno de desarrollo. **/FD** no se expone en la salida de `cl /?`.

Si no habilita la opción **/GM** en desuso en el entorno de desarrollo, se usa **/FD** . **/FD** garantiza que el archivo. IDB tiene suficiente información de dependencia. **/FD** solo se usa en el entorno de desarrollo y no debe usarse desde la línea de comandos o un script de compilación.

## <a name="see-also"></a>Consulte también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
