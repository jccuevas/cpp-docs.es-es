---
title: Advertencia PRJ0049 al compilar el proyecto
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: e857a50215dc7516c0e2ec45a97638c76f40f43b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191759"
---
# <a name="project-build-warning-prj0049"></a>Advertencia PRJ0049 al compilar el proyecto

El destino '\<Reference > ' al que se hace referencia requiere .NET Framework \<MinFrameworkVersion > y no podrá ejecutarse en la plataforma de destino de este proyecto.

Las aplicaciones creadas con Visual Studio 2008 pueden especificar la versión de .NET Framework de destino. Si agrega una referencia a un ensamblado o proyecto que depende de una versión de la .NET Framework posterior a la versión de destino, recibirá esta advertencia en tiempo de compilación.

### <a name="to-correct-this-warning"></a>Para corregir esta advertencia

1. Elija alguna de las acciones siguientes:

   - Cambie la plataforma de destino en el cuadro de diálogo **páginas de propiedades** del proyecto para que sea posterior o igual a la versión de .NET Framework mínima de todos los ensamblados y proyectos a los que se hace referencia. Para obtener más información, vea [Agregar referencias](../../build/adding-references-in-visual-cpp-projects.md).

   - Quite la referencia al ensamblado o proyecto que tenga una versión de .NET Framework mínima posterior a la del marco de destino. Estos elementos se marcarán con un icono de advertencia en las **páginas de propiedades**del proyecto.

## <a name="see-also"></a>Consulte también

[Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
