---
title: Error PRJ0016 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: ada89b074fd8e0c2bfc75ba833e9c5966a145312
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359428"
---
# <a name="project-build-error-prj0016"></a>Error PRJ0016 al compilar el proyecto

Configuración de seguridad del usuario impide que el proceso que se está creando. Esta configuración es necesaria para la compilación.

Se registran en como un usuario que no tiene permisos para crear procesos mediante un proceso. Debe cambiar los niveles de permisos para esta cuenta de usuario, o póngase en contacto con el Administrador de cuentas.

Este error puede producirse también si se establece la clave del registro siguiente:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Para resolver este error, elimine la clave RestrictRun. Si se necesita esta clave del registro, anexar **vcspawn.exe** a la lista de entradas de la clave.

Otra causa de este error es que la configuración de directivas no incluye VCSpawn.exe en la clave del Registro HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun como programa de ventana permitido para esta cuenta de usuario.

Para obtener más información, consulte [cumplir con la configuración de directiva de sistema](https://msdn.microsoft.com/library/aa372139), en la sección sobre "Ejecutar sólo aplicaciones permitidas de Windows".