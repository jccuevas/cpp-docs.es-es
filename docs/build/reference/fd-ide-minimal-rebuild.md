---
title: /FD (Recompilación mínima de IDE)
ms.date: 11/04/2016
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 323a0045ab11f23ab996d5179a135d0eb4184f20
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817444"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Recompilación mínima de IDE)

**/FD** no se expone a los usuarios, excepto en el [línea de comandos](command-line-property-pages.md) página de propiedades de un proyecto de C++ **páginas de propiedades** cuadro de diálogo si y solo si [/Gm (habilitar recompilación mínima)](gm-enable-minimal-rebuild.md) también no se selecciona. **/FD** no tiene ningún efecto distinto del entorno de desarrollo. **/FD** no se expone en la salida de **cl /?**.

Si no habilita **/Gm** en el entorno de desarrollo **/FD** se usará. **/FD** garantiza que el archivo .idb tiene suficiente información de dependencia. **/FD** solo se utiliza en el entorno de desarrollo, y no debe usarse desde la línea de comandos o un script de compilación.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
