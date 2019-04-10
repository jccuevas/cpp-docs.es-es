---
title: /FD (Recompilación mínima de IDE)
ms.date: 04/08/2019
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: ac63b021dc0cb9ee5964af7fa2e168f710653979
ms.sourcegitcommit: 39debf8c525c3951af6913ee5e514617658f8859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424058"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Recompilación mínima de IDE)

**/FD** solo se expone a los usuarios de la [línea de comandos](command-line-property-pages.md) página de propiedades de un C++ del proyecto **páginas de propiedades** cuadro de diálogo. Está disponible si y solo si está en desuso y desactivada de forma predeterminada [/Gm (habilitar recompilación mínima)](gm-enable-minimal-rebuild.md) no está seleccionada la opción. **/FD** no tiene ningún efecto distinto del entorno de desarrollo. **/FD** no se exponen en la salida de `cl /?`.

Si no habilita el desuso **/Gm** opción en el entorno de desarrollo **/FD** se utiliza. **/FD** garantiza que el archivo .idb tiene suficiente información de dependencia. **/FD** solo se utiliza en el entorno de desarrollo, y no debería utilizarse desde la línea de comandos o un script de compilación.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
