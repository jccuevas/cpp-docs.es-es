---
title: -FD (recompilación mínima de IDE) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 474602ce51ff9eb84f54d7580104f641d9b5b2a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396199"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Recompilación mínima de IDE)

**/FD** no se expone a los usuarios, excepto en el [línea de comandos](../../ide/command-line-property-pages.md) página de propiedades de un proyecto de C++ **páginas de propiedades** cuadro de diálogo si y solo si [/Gm (habilitar recompilación mínima)](../../build/reference/gm-enable-minimal-rebuild.md) también no se selecciona. **/FD** no tiene ningún efecto distinto del entorno de desarrollo. **/FD** no se expone en la salida de **cl /?**.

Si no habilita **/Gm** en el entorno de desarrollo **/FD** se usará. **/FD** garantiza que el archivo .idb tiene suficiente información de dependencia. **/FD** solo se utiliza en el entorno de desarrollo, y no debe usarse desde la línea de comandos o un script de compilación.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](../../build/reference/output-file-f-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)