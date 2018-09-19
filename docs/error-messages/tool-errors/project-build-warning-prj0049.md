---
title: Advertencia PRJ0049 de compilar el del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 169ba63318f630ac6a63b18d34fd6a7d829f4f90
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110892"
---
# <a name="project-build-warning-prj0049"></a>Advertencia PRJ0049 al compilar el proyecto

Destino que se hace referencia '\<referencia >' requiere .NET Framework \<MinFrameworkVersion > y no se puede ejecutar en .NET framework de destino de este proyecto

Las aplicaciones creadas con Visual Studio 2008 pueden especificar qué versión de .NET Framework deben tener como destino. Si agrega una referencia a un ensamblado o proyecto que dependa de una versión de .NET Framework posterior a la versión de destino, obtendrá esta advertencia en tiempo de compilación.

### <a name="to-correct-this-warning"></a>Para corregir esta advertencia

1. Elija una de las siguientes opciones:

   - Cambiar el marco de destino en el proyecto **páginas de propiedades** cuadro de diálogo para que sea posterior o igual a la versión mínima del marco de trabajo de todos los ensamblados referenciados y proyectos. Para obtener más información, consulte [agregar referencias](../../ide/adding-references-in-visual-cpp-projects.md).

   - Quite la referencia al ensamblado o proyecto que tiene una versión mínima del marco posterior a la plataforma de destino. Estos elementos se marcan con un icono de advertencia en el proyecto **páginas de propiedades**.

## <a name="see-also"></a>Vea también

[Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)