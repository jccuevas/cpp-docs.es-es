---
title: Error PRJ0016 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0016
dev_langs:
- C++
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ceb004cba243d6e2e9c44aadcaa40670ef7a0bbb
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890262"
---
# <a name="project-build-error-prj0016"></a>Error PRJ0016 al compilar el proyecto

Configuración de seguridad del usuario impide que el proceso que se está creando. Esta configuración es necesaria para la compilación.

Se registran en como un usuario que no tiene permisos para crear procesos mediante un proceso. Debe cambiar los niveles de permisos para esta cuenta de usuario, o póngase en contacto con el Administrador de cuentas.

Este error puede producirse también si se establece la clave del registro siguiente:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Para resolver este error, elimine la clave RestrictRun. Si se necesita esta clave del registro, anexar **vcspawn.exe** a la lista de entradas de la clave.

Otra causa de este error es que la configuración de directivas no incluye VCSpawn.exe en la clave del Registro HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun como programa de ventana permitido para esta cuenta de usuario.

Para obtener más información, consulte [cumplir con la configuración de directiva de sistema](https://msdn.microsoft.com/library/aa372139), en la sección sobre "Ejecutar sólo aplicaciones permitidas de Windows".