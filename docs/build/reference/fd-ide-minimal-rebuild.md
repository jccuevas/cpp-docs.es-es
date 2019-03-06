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
ms.openlocfilehash: 0685df0baf14685bd24b8390dd58b382ae5ac506
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422057"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Recompilación mínima de IDE)

**/FD** no se expone a los usuarios, excepto en el [línea de comandos](../../ide/command-line-property-pages.md) página de propiedades de un proyecto de C++ **páginas de propiedades** cuadro de diálogo si y solo si [/Gm (habilitar recompilación mínima)](../../build/reference/gm-enable-minimal-rebuild.md) también no se selecciona. **/FD** no tiene ningún efecto distinto del entorno de desarrollo. **/FD** no se expone en la salida de **cl /?**.

Si no habilita **/Gm** en el entorno de desarrollo **/FD** se usará. **/FD** garantiza que el archivo .idb tiene suficiente información de dependencia. **/FD** solo se utiliza en el entorno de desarrollo, y no debe usarse desde la línea de comandos o un script de compilación.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](../../build/reference/output-file-f-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
