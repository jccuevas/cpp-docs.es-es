---
title: Error PRJ0050 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb3949ea0db2f1667aecf1aeeefd922b192cbf41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100596"
---
# <a name="project-build-error-prj0050"></a>Error PRJ0050 al compilar el proyecto

No se pudo registrar la salida. Asegúrese de que tener los permisos adecuados para modificar el registro.

El sistema de compilación de Visual C++ no pudo registrar la salida de la compilación (dll o .exe). Debe haber iniciado sesión como administrador para modificar el registro.

Si va a compilar un archivo .dll, puede intentar registrar el archivo .dll manualmente utilizando regsvr32.exe, esto debería mostrar información sobre el motivo del error de la compilación.

Si no se genera un archivo .dll, examine el registro de compilación para el comando que se produce un error.