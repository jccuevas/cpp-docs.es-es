---
title: -FD (recompilación mínima de IDE) | Documentos de Microsoft
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
ms.openlocfilehash: 18e31955b131e4ca22d23013565e53f83493275d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Recompilación mínima de IDE)
**/FD** no se expone a los usuarios, excepto en el [línea de comandos](../../ide/command-line-property-pages.md) página de propiedades de un proyecto de C++ **páginas de propiedades** cuadro de diálogo si y solo si [/Gm (habilitar recompilación mínima)](../../build/reference/gm-enable-minimal-rebuild.md) no está también seleccionado. **/FD** no tiene ningún efecto distinto del entorno de desarrollo. **/FD** no se expone en la salida de **cl /?**.  
  
 Si no habilita **/Gm** en el entorno de desarrollo, **/FD** se usará. **/FD** garantiza que el archivo .idb tiene suficiente información de dependencia. **/FD** solo se utiliza en el entorno de desarrollo, y no debe usarse desde la línea de comandos o un script de compilación.  
  
## <a name="see-also"></a>Vea también  
 [Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)